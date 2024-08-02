using System;
using System.Drawing;
using System.Windows.Forms;

namespace SimpleCarGame
{
    public partial class Form1 : Form
    {
        private const int CarSpeed = 10;

        public Form1()
        {
            InitializeComponent();
            this.KeyPreview = true;
            this.KeyDown += new KeyEventHandler(Form1_KeyDown);
            this.Load += new EventHandler(Form1_Load);
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            // Set the form's properties
            this.Width = 800;
            this.Height = 600;

            // Set the car's properties
            carPictureBox.BackColor = Color.Transparent;
            carPictureBox.Image = Properties.Resources.CarImage; // Ensure you add an image to resources
            carPictureBox.SizeMode = PictureBoxSizeMode.StretchImage;

            // Set the timer's properties
            gameTimer.Interval = 20; // 20 milliseconds for smoother movement
            gameTimer.Tick += new EventHandler(GameTimer_Tick);
            gameTimer.Start();
        }

        private void Form1_KeyDown(object sender, KeyEventArgs e)
        {
            switch (e.KeyCode)
            {
                case Keys.Left:
                    if (carPictureBox.Left > 0)
                    {
                        carPictureBox.Left -= CarSpeed;
                    }
                    break;
                case Keys.Right:
                    if (carPictureBox.Right < this.ClientSize.Width)
                    {
                        carPictureBox.Left += CarSpeed;
                    }
                    break;
            }
        }

        private void GameTimer_Tick(object sender, EventArgs e)
        {
            // You can add code here to handle game updates, like movement or collisions.
            // For now, it’s just keeping the timer running.
        }
    }
}
