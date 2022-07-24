# BauCuaC#-Winform.Net
Bầu Cua Game 2023 - Code By Rioxer 

#FullCode
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace BauCua
{

    // CODE BY RIOXER
    public partial class Form1 : Form
    {
        string pathImg; // Img Bầu Cua
        int choose; // Chọn 
        int money;  // Tiền cược
        int newMoney = 10000;   // Money Player
        Random rand = new Random();

        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            Init();
        }

        // Khởi Tạo
        private void Init()
        {
            pathImg = Application.StartupPath + @"\img\";
            pcResult1.Image = Image.FromFile(pathImg + "5.png");
            pcResult2.Image = Image.FromFile(pathImg + "2.png");
            pcResult3.Image = Image.FromFile(pathImg + "3.png");

            // Gán label Money cho biến tiền mặc định
            lbMoney.Text = newMoney.ToString();
        }

        // Reset clear choose & money default
        private void Reset()
        {
            newMoney = 10000;
            lbMoney.Text = newMoney.ToString();
            chooseBox.SelectedIndex = -1;     
        }

        private void chooseBox_SelectedIndexChanged(object sender, EventArgs e)
        {
            ComboBox cb = sender as ComboBox;
            choose = int.Parse(cb.SelectedIndex.ToString());  
            
        }

        private void playBtn_Click(object sender, EventArgs e)
        {
            string kq;
            if(newMoney < money)            // Kiểm tra điều kiện đặt cược
            {
                MessageBox.Show("Mức cược quá lớn !!\n" + "Mời chọn lại !!!");
            }
            else
            {
                // Tạo Random Xíu Ngầu
                int num1 = rand.Next(1, 7);
                int num2 = rand.Next(1, 7);
                int num3 = rand.Next(1, 7);

                // show Result Img
                pcResult1.Image = Image.FromFile(pathImg + num1.ToString() + ".png");
                pcResult2.Image = Image.FromFile(pathImg + num2.ToString() + ".png");
                pcResult3.Image = Image.FromFile(pathImg + num3.ToString() + ".png");

                // Kiểm tra Luật chơi
                if (choose == 1)
                {
                    // Có 1 con là được
                    if (num1 == choose || num2 == choose || num3 == choose)
                    {
                        // Có 2 con tiền gấp đôi
                        if ((num1 == choose && num2 == choose) || (num2 == choose && num3 == choose) || (num1 == choose && num3 == choose))
                        {
                            // Có 3 con tiền gấp 3
                            if (num1 == choose && num2 == choose && num3 == choose)
                            {
                                newMoney = newMoney + money * 3;
                                kq = "Vui Xuân 2023 \n" + "Tiền của bạn là: " + newMoney;
                                MessageBox.Show(kq.ToString());
                                lbMoney.Text = newMoney.ToString();
                            }
                            else
                            {
                                newMoney = newMoney + money * 2;
                                kq = "Có 2 Nai \n" + "Tiền của bạn là: " + newMoney;
                                MessageBox.Show(kq.ToString());
                                lbMoney.Text = newMoney.ToString();
                            }
                        }
                        else
                        {
                            newMoney = newMoney + money;
                            kq = "Có 1 Nai \n" + "Tiền của bạn là: " + newMoney;
                            MessageBox.Show(kq.ToString());
                            lbMoney.Text = newMoney.ToString();
                        }
                    }
                    else        // Không có con nào thì trừ tiền
                    {
                        newMoney = newMoney - money;
                        kq = "Méo Có Nai \n" + "Tiền của bạn là: " + newMoney;
                        MessageBox.Show(kq.ToString());

                        // Kiểm tra hết tiền 
                        if (newMoney == 0)
                        {
                            MessageBox.Show("Bạn đã hết tiền !!!");
                            Reset();
                        }
                        else
                        {
                            lbMoney.Text = newMoney.ToString();
                        }
                    }

                }
                else if (choose == 2)
                {
                    if (num1 == choose || num2 == choose || num3 == choose)
                    {
                        if ((num1 == choose && num2 == choose) || (num2 == choose && num3 == choose) || (num1 == choose && num3 == choose))
                        {
                            if (num1 == choose && num2 == choose && num3 == choose)
                            {
                                newMoney = newMoney + money * 3;
                                kq = "Vui Xuân 2023 \n" + "Tiền của bạn là: " + newMoney;
                                MessageBox.Show(kq.ToString());
                                lbMoney.Text = newMoney.ToString();
                            }
                            else
                            {
                                newMoney = newMoney + money * 2;
                                kq = "Có 2 Bầu \n" + "Tiền của bạn là: " + newMoney;
                                MessageBox.Show(kq.ToString());
                                lbMoney.Text = newMoney.ToString();
                            }
                        }
                        else
                        {
                            newMoney = newMoney + money;
                            kq = "Có 1 Bầu \n" + "Tiền của bạn là: " + newMoney;
                            MessageBox.Show(kq.ToString());
                            lbMoney.Text = newMoney.ToString();
                        }
                    }
                    else
                    {
                        newMoney = newMoney - money;
                        kq = "Méo Có Bầu \n" + "Tiền của bạn là: " + newMoney;
                        MessageBox.Show(kq.ToString());
                        if (newMoney == 0)
                        {
                            MessageBox.Show("Bạn đã hết tiền !!!");
                            Reset();
                        }
                        else
                        {
                            lbMoney.Text = newMoney.ToString();
                        }
                    }
                }
                else if (choose == 3)
                {
                    if (num1 == choose || num2 == choose || num3 == choose)
                    {
                        if ((num1 == choose && num2 == choose) || (num2 == choose && num3 == choose) || (num1 == choose && num3 == choose))
                        {
                            if (num1 == choose && num2 == choose && num3 == choose)
                            {
                                newMoney = newMoney + money * 3;
                                kq = "Vui Xuân 2023 \n" + "Tiền của bạn là: " + newMoney;
                                MessageBox.Show(kq.ToString());
                                lbMoney.Text = newMoney.ToString();
                            }
                            else
                            {
                                newMoney = newMoney + money * 2;
                                kq = "Có 2 Gà \n" + "Tiền của bạn là: " + newMoney;
                                MessageBox.Show(kq.ToString());
                                lbMoney.Text = newMoney.ToString();
                            }
                        }
                        else
                        {
                            newMoney = newMoney + money;
                            kq = "Có 1 Gà \n" + "Tiền của bạn là: " + newMoney;
                            MessageBox.Show(kq.ToString());
                            lbMoney.Text = newMoney.ToString();
                        }
                    }
                    else
                    {
                        newMoney = newMoney - money;
                        kq = "Méo Có Gà \n" + "Tiền của bạn là: " + newMoney;
                        MessageBox.Show(kq.ToString());
                        if (newMoney == 0)
                        {
                            MessageBox.Show("Bạn đã hết tiền !!!");
                            Reset();
                        }
                        else
                        {
                            lbMoney.Text = newMoney.ToString();
                        }
                    }
                }
                else if (choose == 4)
                {
                    if (num1 == choose || num2 == choose || num3 == choose)
                    {
                        if ((num1 == choose && num2 == choose) || (num2 == choose && num3 == choose) || (num1 == choose && num3 == choose))
                        {
                            if (num1 == choose && num2 == choose && num3 == choose)
                            {
                                newMoney = newMoney + money * 3;
                                kq = "Vui Xuân 2023 \n" + "Tiền của bạn là: " + newMoney;
                                MessageBox.Show(kq.ToString());
                                lbMoney.Text = newMoney.ToString();
                            }
                            else
                            {
                                newMoney = newMoney + money * 2;
                                kq = "Có 2 Cá \n" + "Tiền của bạn là: " + newMoney;
                                MessageBox.Show(kq.ToString());
                                lbMoney.Text = newMoney.ToString();
                            }
                        }
                        else
                        {
                            newMoney = newMoney + money;
                            kq = "Có 1 Cá \n" + "Tiền của bạn là: " + newMoney;
                            MessageBox.Show(kq.ToString());
                            lbMoney.Text = newMoney.ToString();
                        }
                    }
                    else
                    {
                        newMoney = newMoney - money;
                        kq = "Méo Có Cá \n" + "Tiền của bạn là: " + newMoney;
                        MessageBox.Show(kq.ToString());
                        if (newMoney == 0)
                        {
                            MessageBox.Show("Bạn đã hết tiền !!!");
                            Reset();
                        }
                        else
                        {
                            lbMoney.Text = newMoney.ToString();
                        }
                    }
                }
                else if (choose == 5)
                {
                    if (num1 == choose || num2 == choose || num3 == choose)
                    {
                        if ((num1 == choose && num2 == choose) || (num2 == choose && num3 == choose) || (num1 == choose && num3 == choose))
                        { 
                            if (num1 == choose && num2 == choose && num3 == choose)
                            {
                                newMoney = newMoney + money * 3;
                                kq = "Vui Xuân 2023 \n" + "Tiền của bạn là: " + newMoney;
                                MessageBox.Show(kq.ToString());
                                lbMoney.Text = newMoney.ToString();
                            }
                            else
                            {
                                newMoney = newMoney + money * 2;
                                kq = "Có 2 Cua \n" + "Tiền của bạn là: " + newMoney;
                                MessageBox.Show(kq.ToString());
                                lbMoney.Text = newMoney.ToString();
                            }
                        }
                        else
                        {
                            newMoney = newMoney + money;
                            kq = "Có 1 Cua \n" + "Tiền của bạn là: " + newMoney;
                            MessageBox.Show(kq.ToString());
                            lbMoney.Text = newMoney.ToString();
                        }
                    }
                    else
                    {
                        newMoney = newMoney - money;
                        kq = "Méo Có Cua \n" + "Tiền của bạn là: " + newMoney;
                        MessageBox.Show(kq.ToString());
                        if (newMoney == 0)
                        {
                            MessageBox.Show("Bạn đã hết tiền !!!");
                            Reset();
                        }
                        else
                        {
                            lbMoney.Text = newMoney.ToString();
                        }
                    }
                }
                else if (choose == 6)
                {
                    if (num1 == choose || num2 == choose || num3 == choose)
                    {
                        if ((num1 == choose && num2 == choose) || (num2 == choose && num3 == choose) || (num1 == choose && num3 == choose))
                        {
                            if (num1 == choose && num2 == choose && num3 == choose)
                            {
                                newMoney = newMoney + money * 3;
                                kq = "Vui Xuân 2023 \n" + "Tiền của bạn là: " + newMoney;
                                MessageBox.Show(kq.ToString());
                                lbMoney.Text = newMoney.ToString();
                            }
                            else
                            {
                                newMoney = newMoney + money * 2;
                                kq = "Có 2 Tôm \n" + "Tiền của bạn là: " + newMoney;
                                MessageBox.Show(kq.ToString());
                                lbMoney.Text = newMoney.ToString();
                            }
                        }
                        else
                        {
                            newMoney = newMoney + money;
                            kq = "Có 1 Tôm \n" + "Tiền của bạn là: " + newMoney;
                            MessageBox.Show(kq.ToString());
                            lbMoney.Text = newMoney.ToString();
                        }
                    }
                    else
                    {
                        newMoney = newMoney - money;
                        kq = "Méo Có Tôm \n" + "Tiền của bạn là: " + newMoney;
                        MessageBox.Show(kq.ToString());
                        if (newMoney == 0)
                        {
                            MessageBox.Show("Bạn đã hết tiền !!!");
                            Reset();
                        }
                        else
                        {
                            lbMoney.Text = newMoney.ToString();
                        }
                    }
                }
            }

        }

        private void moneyBox_SelectedIndexChanged(object sender, EventArgs e)
        {
            ComboBox cb = sender as ComboBox;
            money = int.Parse(cb.SelectedItem.ToString());
        }

        // Quit Game 
        private void quitBtn_Click(object sender, EventArgs e)
        {
            DialogResult dr = MessageBox.Show("Bạn Muốn Thoát Game ?", "Message Quit Game", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
            if (dr == DialogResult.Yes)
            {
                Application.ExitThread();
            }
            else
            {
                
            }
        }
    }
}
