using System;
using System.IO;
using System.Security.Cryptography.X509Certificates;
using System.Text;
using System.Text.RegularExpressions;
using System.Windows.Forms;


namespace lab_exercise_2
{
    public partial class Form1 : Form
    {
        String fileContent;

        StringBuilder buffer = new StringBuilder();


        public Form1()
        {
            InitializeComponent();

        }

        private void button1_Click(object sender, EventArgs e)
        {

        }

        private void button1_Click_1(object sender, EventArgs e)
        {
            OpenFileDialog openFile = new OpenFileDialog();
            if (openFile.ShowDialog() == DialogResult.OK)
            {
                this.fileContent = File.ReadAllText(openFile.FileName, Encoding.ASCII);
                this.textBox1.Text = this.fileContent;
            }
        }

        private void button2_Click(object sender, EventArgs e)
        {
            this.textBox2.Text = this.fileContent.Substring(1, 5);
        }

        private void button3_Click(object sender, EventArgs e)
        {
            this.textBox3.Text = this.fileContent.Substring(10);
        }

        private void button4_Click(object sender, EventArgs e)
        {
            string con = this.textBox2.Text + " " + this.textBox3.Text;
            this.textBox4.Text = con;
        }

        private void panel1_Paint(object sender, PaintEventArgs e)
        {

        }

        private void button5_Click(object sender, EventArgs e)
        {

            string[] spl = this.textBox1.Text.Split();
            foreach (string item in spl)
            {
                this.richTextBox1.AppendText(item);
            }
        }

        private void textBox1_TextChanged(object sender, EventArgs e)
        {

        }

        private void textBox5_TextChanged(object sender, EventArgs e)
        {

        }

        private void button6_Click(object sender, EventArgs e)
        {
            string str1 = this.textBox5.Text;
            string str2 = this.textBox10.Text;
            string file = this.fileContent;
            string ss = file.Replace(str1, str2);
            this.textBox6.Text = ss;
        }

        private void button7_Click(object sender, EventArgs e)
        {
            String file1 = this.fileContent.ToLower();

            this.textBox7.Text = file1;
        }

        private void button8_Click(object sender, EventArgs e)
        {
            String file1 = this.fileContent.ToUpper();

            this.textBox8.Text = file1;
        }

        private void button9_Click(object sender, EventArgs e)
        {
            String file1 = this.fileContent.Trim();

            this.textBox9.Text = file1;
        }

        private void flowLayoutPanel1_Paint(object sender, PaintEventArgs e)
        {

        }

        private void button10_Click(object sender, EventArgs e)
        {
            var buffer = new StringBuilder("Hello, how are you?");
            MessageBox.Show("buffer " + buffer + "\nLength" + buffer.Length + "\nCapacity" + buffer.Capacity);
            buffer.EnsureCapacity(75);
            MessageBox.Show("New capacity" + buffer.Capacity);
            MessageBox.Show("New length " + buffer.Length);


            for (int i = 0; i < buffer.Length; ++i)
            {
                this.textBox11.AppendText(buffer.ToString());
                Console.Write(buffer[i]);
            }
            Console.WriteLine();
        }

        private void button11_Click(object sender, EventArgs e)
        {
            object objectValue = "hello";
            var stringValue = "good bye";
            char[] characterArray = { 'a', 'b', 'c', 'd', 'e', 'f' };
            var booleanValue = true;
            var characterValue = 'Z';
            var integerValue = 7;
            var longValue = 1000000L;
            var floatValue = 2.5F;
            var doubleValue = 33.333;

            buffer.Append(objectValue); buffer.Append(" ");
            buffer.Append(stringValue); buffer.Append(" ");
            buffer.Append(characterArray); buffer.Append(" ");
            buffer.Append(characterArray, 0, 3); buffer.Append(" ");
            buffer.Append(booleanValue); buffer.Append(" ");
            buffer.Append(characterValue); buffer.Append(" ");
            buffer.Append(integerValue); buffer.Append(" ");
            buffer.Append(longValue); buffer.Append(" ");
            buffer.Append(floatValue); buffer.Append(" ");
            buffer.Append(doubleValue);
            MessageBox.Show($"buffer = {buffer}");
            buffer.Remove(10, 1);
            MessageBox.Show($"buffer = {buffer}");
        }

        private void button12_Click(object sender, EventArgs e)
        {
            this.buffer.Remove(10, 2);
            MessageBox.Show($"buffer = {buffer}");
        }

        private void button13_Click(object sender, EventArgs e)
        {
            this.buffer.Remove(4, 4);
            MessageBox.Show($"buffer = {buffer}");
        }

        private void button14_Click(object sender, EventArgs e)
        {
            char letter = char.Parse(textBox12.Text);
            if (char.IsDigit(letter))
            {
                MessageBox.Show($"yes it is a digit {letter}");
            }
            else
            {
                MessageBox.Show($"No it is not a digit {letter}");
            }
        }

        private void richTextBox2_TextChanged(object sender, EventArgs e)
        {

        }

        private void button15_Click(object sender, EventArgs e)
        {
            char letter = char.Parse(textBox12.Text);
            if (char.IsLetterOrDigit(letter))
            {
                MessageBox.Show($"yes it is a digitOraletter {letter}");
            }
            else
            {
                MessageBox.Show($"No it is not a digitOraletter {letter}");
            }
        }

        private void button17_Click(object sender, EventArgs e)
        {
            char letter = char.Parse(textBox12.Text);


            if (!char.IsDigit(letter))
            {
                MessageBox.Show($"To upper case {letter.ToString().ToUpper()} ");
            }


        }

        private void button16_Click(object sender, EventArgs e)
        {
            char letter = char.Parse(textBox12.Text);
            if (char.IsLower(letter) || !char.IsDigit(letter))
            {
                MessageBox.Show($"yes it is a it is lower letter {letter}");
            }
            else
            {
                MessageBox.Show($"No it is not a lower letter {letter}");
            }
        }

        private void button18_Click(object sender, EventArgs e)
        {
            Regex exp = new Regex(@"\w.*\d[0-35-9]-\d\d-\d\d");
            string string1 = "Jan's birthday is 05-12-75\n" +
            "Dave's birthday is 11-04-68\n" +
            "Yoha's birthday is 41-04-68\n" +
            "Jhon's birthday is 04-28-73\n" +
            "Joe's birthday is 12-17-77";
            foreach (Match ma in exp.Matches(string1))
                MessageBox.Show(ma.ToString());
        }
        private void button20_Click(object sender, EventArgs e)
        {
            Regex exp = new Regex(@"j[^0]\w.*\d[1-35-9]-\d\d-\d\d");
            string string1 = "Jan's birthday is 05-12-75\n" +
            "Dave's birthday is 11-04-68\n" +
            "Yoha's birthday is 41-04-68\n" +
            "Jhon's birthday is 04-28-73\n" +
            "Joe's birthday is 12-17-77";
            foreach (Match ma in exp.Matches(string1))
                MessageBox.Show(ma.ToString());
        }
        private void button19_Click(object sender, EventArgs e)
        {
            Regex exp = new Regex(@"\w.*\d[0-35-9]-\d\d-\d\d");
            string string1 = "Jan's birthday is 05-12-75\n" +
            "Dave's birthday is 11-04-68\n" +
            "Yoha's birthday is 41-04-68\n" +
            "Jhon's birthday is 04-28-73\n" +
            "Joe's birthday is 12-17-77";

            MatchCollection matches = exp.Matches(string1);

            String message = "";

            if (matches.Count > 0)
            {
                foreach (Match match in matches)
                {
                    message += match.Value + "\n";
                }
            }
            else
            {
                message = "no match";
            }
            MessageBox.Show(message);

        }

        private void button21_Click(object sender, EventArgs e)
        {

            string id = textBox13.Text;
            Regex idregex = new Regex(@"^UGR/\d{4}/\d{2}$");
            if (idregex.IsMatch(id))
            {
                MessageBox.Show("it is matched");
            }
            else
            {
                MessageBox.Show("it is not matched");
            }


        }

        private void button22_Click(object sender, EventArgs e)
        {
            string email = textBox14.Text;
            Regex emailregex = new Regex(@"^[^@\s]+@[^@\s]+\.(com|net|org|gov)$", RegexOptions.IgnoreCase);
            if (emailregex.IsMatch(email))
            {
                MessageBox.Show("it is matched");
            }
            else
            {
                MessageBox.Show("it is not matched");
            }
        }

        private void panel2_Paint(object sender, PaintEventArgs e)
        {

        }

        private void Form1_Load(object sender, EventArgs e)
        {

        }
    }
}