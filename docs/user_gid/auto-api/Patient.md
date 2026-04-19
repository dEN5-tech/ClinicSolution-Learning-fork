using System;

namespace ClinicCore
{
    public class Patient
    {
        public string FullName { get; set; }

        public DateTime BirthDate { get; set; }

        /// <summary>

        /// Метод вычисляет возраст пациента.

        /// Если день рождения еще не наступил в этом году - возраст уменьшается на 1.

        /// </summary>
        public double Weight { get; set; } // Вес в кг

        /// <summary>

        /// Группа крови пациента.

        /// </summary>

        public string BloodType { get; set; }


        public double Height { get; set; } // Рост в метрах

        /// <summary>

        /// Вычисляет Индекс Массы Тела (ИМТ/BMI) пациента.

        /// </summary>

        /// <remarks>

        /// ИМТ рассчитывается по формуле: вес (кг) / рост (м) в квадрате.

        /// Используется для первичной диагностики веса.

        /// </remarks>

        /// <returns>Числовое значение ИМТ.</returns>

        /// <exception cref="DivideByZeroException">Выбрасывается, если рост (Height) равен нулю или отрицательный.</exception>

        public double CalculateBMI()
        {
            if (Height <= 0)
                throw new DivideByZeroException("Height must be greater than zero.");
            return Weight / (Height * Height);
        }


        /// <summary>

        /// Вычисляет возраст.

        /// <br/>

        /// <strong>Внимание:</strong> Метод использует локальное время сервера.

        /// </summary>

        public int CalculateAge()
        {
            var today = DateTime.Today;

            var age = today.Year - BirthDate.Year;

            // Если текущая дата меньше дня рождения в текущем году, вычитаем год

            if (BirthDate.Date > today.AddYears(-age))
                age--;
            return age;
        }
    }
}
