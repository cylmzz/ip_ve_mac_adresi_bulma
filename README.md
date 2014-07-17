ip_ve_mac_adresi_bulma
======================
using System;

using System.Collections.Generic;

using System.ComponentModel;

using System.Data;

using System.Drawing;

using System.Linq;

using System.Text;

using System.Threading.Tasks;

using System.Windows.Forms;

using System.Net;

using System.Net.NetworkInformation;

namespace ip_ve_mac_adresi_tespit_etme

{

    public partial class Form1 : Form
    
    {
        public Form1()
        
        {
        
            InitializeComponent();
            
        }

        private void Form1_Load(object sender, EventArgs e)
        
        {

            foreach (NetworkInterface networkInterface in NetworkInterface.GetAllNetworkInterfaces())
	  {

//foreach ; bir döngü fonksiyonudur.Bir dizi belirten ifadenin veya bir koleksiyonun her elemanı için yapısındaki kodları //çalıştıran bir döngüdür.Tüm network arayüzlerinden çalıştığı bilgisayarın arayüzünü döndürür.

                var macAddress = networkInterface.GetPhysicalAddress().ToString();

// var ; int,float,double.. gibi değişken tanımlarını her değişkenin başına tek tek yazmak yerine hepsinin başına var //yazarak durumu basitçe çözebiliriz.

                if (macAddress != string.Empty)
                {
                    listBox1.Items.Add("Mac Adres : " + macAddress);
                }
            }

            IPAddress[] ipHostAddress = Dns.GetHostAddresses(Dns.GetHostName());

            for (int i = 0; i < ipHostAddress.Length; i++)
            {
                listBox1.Items.Add("Lokal IP Adres : " + ipHostAddress[i].ToString());
            }
        }
    }
}
