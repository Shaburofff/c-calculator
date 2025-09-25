# c-calculator
using System;
using System.Drawing;
using System.Windows.Forms;

namespace Form1
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            this.Text = $"short: {short.MinValue}..{short.MaxValue}, размер: {sizeof(short)} байт | " +
                       $"decimal: {decimal.MinValue}..{decimal.MaxValue}, размер: {sizeof(decimal)} байт";
        }
        private void button1Calculate_Click(object sender, EventArgs e)
        {
            try
            {
                var operand1 = short.Parse(textBox1.Text);
                decimal operand2 = decimal.Parse(textBox2.Text);
                string operation = textBox3.Text.Trim();

                decimal result = 0;

                result = operation == "+" ? operand1 + operand2 :
                         operation == "-" ? operand1 - operand2 :
                         operation == "*" ? operand1 * operand2 :
                         operation == "/" ? operand1 / operand2 :
                         throw new ArgumentException("Неизвестная операция");

                label1.Text = result.ToString();
            }
            catch (Exception ex)
            {
                MessageBox.Show($"Ошибка: {ex.Message}", "Ошибка ввода", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
        }
    }
}
