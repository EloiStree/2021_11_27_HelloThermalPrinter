# 2021_11_27_HelloThermalPrinter
C31CH51011 - Epson TM-T20

https://stackoverflow.com/questions/32595421/is-it-possible-to-send-a-file-to-a-printer-with-a-batch-file
![image](https://user-images.githubusercontent.com/20149493/143677816-88603add-ec31-43cf-ae53-a3a4d3f66445.png)
´´´notepad /P file.txt´´´



![image](https://user-images.githubusercontent.com/20149493/143677828-97701e82-c7d8-4ee1-ba8f-d089eb2ab20b.png)
"C:\Program Files\LibreOffice\program\soffice.exe" -p "YourFilePAth"


https://stackoverflow.com/questions/2301101/command-line-tool-for-print-picture
![image](https://user-images.githubusercontent.com/20149493/143677870-13463103-d04b-427d-b361-11fc003ae78d.png)
mspaint /pt [image filename]


Print from PRINT command:
https://www.tutorialspoint.com/batch_script/batch_script_printing.htm


Printe

``` csharp

 class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");

            int column=64;
            PrinterUtility.EscPosEpsonCommands.EscPosEpson printer = new PrinterUtility.EscPosEpsonCommands.EscPosEpson(column);
            byte [] bytesValue= new byte[0];
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, printer.Separator());
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, printer.CharSize.DoubleWidth4());
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, printer.FontSelect.FontA());
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, printer.Alignment.Center());
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, Encoding.ASCII.GetBytes("My first ticket\n"));
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, printer.CharSize.DoubleWidth3());
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, Encoding.ASCII.GetBytes("That amazing\n"));
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, printer.CharSize.Nomarl());
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, Encoding.ASCII.GetBytes("Hello Ticket !!!\n"));
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, printer.Alignment.Right());
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, Encoding.ASCII.GetBytes("Ticket numer: 42\n"));
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, printer.Lf());
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, printer.BarCode.Code128("12345"));
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, printer.QrCode.Print("12345", PrinterUtility.Enums.QrCodeSize.Pequeno));
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, printer.Alignment.Center());
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, Encoding.ASCII.GetBytes("-----------"));
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, Encoding.ASCII.GetBytes(DateTime.Now.ToString()));
            bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, printer.Alignment.Left());
           // bytesValue = PrinterUtility.PrintExtensions.AddBytes(bytesValue, CutPage());
            PrinterUtility.PrintExtensions.Print(bytesValue, GetPathOfPrinter());
        }

        public static string GetPathOfPrinter() {
            //https://youtu.be/0mC_yvT3abw?t=658
            return "ESDPRT001";
        }

        private static byte[] CutPage()
        { //source: https://youtu.be/0mC_yvT3abw?t=583
            List<byte> oby = new List<byte>();
            oby.Add(Convert.ToByte(Convert.ToChar(0x1D)));
            oby.Add(Convert.ToByte('v'));
            oby.Add((byte)66);
            oby.Add((byte)3);
            return oby.ToArray();
        }
    }

```
