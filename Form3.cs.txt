using System;
using System.Drawing;
using System.Windows.Forms;

namespace DrawingApp
{
    public partial class Form3 : Form
    {
        private bool drawing;
        private Point previousPoint;

        public Form3()
        {
            InitializeComponent();
            this.drawing = false;
        }

        private void Form3_MouseDown(object sender, MouseEventArgs e)
        {
            if (e.Button == MouseButtons.Left)
            {
                this.drawing = true;
                this.previousPoint = e.Location;
            }
        }

        private void Form3_MouseMove(object sender, MouseEventArgs e)
        {
            if (this.drawing)
            {
                using (Graphics g = this.CreateGraphics())
                {
                    g.DrawLine(Pens.Black, this.previousPoint, e.Location);
                }
                this.previousPoint = e.Location;
            }
        }

        private void Form3_MouseUp(object sender, MouseEventArgs e)
        {
            if (e.Button == MouseButtons.Left)
            {
                this.drawing = false;
            }
        }
    }
}
