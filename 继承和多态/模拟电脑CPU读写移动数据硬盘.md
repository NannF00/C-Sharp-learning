# 

     private static void Main(string[] args)
        {
            //用多态实现,将 移动硬盘或者U盘或者MP3插到电脑上进行读写数据
            MobileStroage md = new MobileMP3Disk();
            CPU cpu= new CPU();
            cpu.Md = md;//必须给cpu的属性赋值
            cpu.CPURead();//cpu中的成员md调用了这个方法
            cpu.CPUWrite();

            Console.ReadKey();
        }
        /// <summary>
        /// 定义所有移动端点的父类
        /// 目的:CPU读取的时候无需判断子类类型,子类可以直接赋值给父类
        /// </summary>
        public abstract class MobileStroage
        {
            public abstract void Read();

            public abstract void Write();
        }

        public class MobileMP3Disk : MobileStroage
        {
            public override void Read()
            {
                Console.WriteLine("MP3 read.");
            }
            public override void Write()
            {
                Console.WriteLine("MP3 write.");
            }
            public void PlayMusic()
            {
                Console.WriteLine("MP3 play music.");
            }
        }

        public class MobileUDisk : MobileStroage
        {
            public override void Read()
            {
                Console.WriteLine("U read.");
            }
            public override void Write()
            {
                Console.WriteLine("U write.");
            }
        }
        public class MobileDisk : MobileStroage
        {
            public override void Write()
            {
                Console.WriteLine("Disk write.");
            }
            public override void Read()
            {
                Console.WriteLine("Disk read.");
            }
        }
        public class CPU
        {
            //给cpu创建一个父类成员
            private MobileStroage _md;
            public MobileStroage Md
            {
                get { return _md; }
                set { _md = value; }
            }
            //cpu不能直接读取子类成员的数据,要调用父类成员的函数读取,这里的参数是那个父类成员
            public void CPURead()
            {
                _md.Read();
            }
            public void CPUWrite()
            {
                _md.Write();
            }
            //或者不用私有字段,使用传参方法
            //public void CPURead(MobileStroage md)
            //{
            //    md.Read();
            //}
        }
