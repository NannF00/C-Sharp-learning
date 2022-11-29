# ToString()是Object类的虚方法,所有类都可以调用.当然也可以改写

    internal class Program
    {
        private static void Main(string[] args)
        {
            Person person = new Person();


            Console.WriteLine(person.ToString()); 
        }

        public class Person
        {
            public string Name { get; set; }
            public int Id { get; set; }
            public override string ToString()
            {
                return "Hello World";
            }
        }
    }
