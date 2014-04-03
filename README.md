doc
===

Documentación

http://msdn.microsoft.com/en-us/library/aa288454(v=vs.71).aspx
http://msdn.microsoft.com/en-us/library/aa288454(v=vs.71).aspx#vcwlkattributestutorialanchor1
http://msdn.microsoft.com/en-us/library/z0w1kczw.aspx
http://msdn.microsoft.com/en-us/library/84c42s56(v=vs.110).aspx


using System;
using System.Collections.Generic;
using System.Linq;
using System.Reflection;
using System.Runtime.CompilerServices;
using System.Text;
using System.Threading.Tasks;
using System.Attribute;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            int numero1 = 10;
            int numero2 = 50;
            
            Suma(numero1,numero2);
            Resta(numero1, numero2);
            Multiplicacion(numero1, numero2);
            Division(numero1, numero2);
            
            Console.Read();
        }
                
        public static Int32 Suma(int numero1, int numero2) 
        {
            obtieneMetaData();
            var resultado = numero1 + numero2;
            return resultado;
        }

        public static Int32 Resta(int numero1, int numero2)
        {
            obtieneMetaData();
            var resultado = numero1 - numero2;
            return resultado;
        }

        public static Int32 Multiplicacion(int numero1, int numero2)
        {
            obtieneMetaData();
            var resultado = numero1 * numero2;
            return resultado;
        }

        [AttributeUsage(AttributeTargets.All)]
        public static Int32 Division(int numero1, int numero2)
        {
            obtieneMetaData();
            var resultado = numero1 / numero2;
            return resultado;
        }

        static void obtieneMetaData([CallerMemberName] string Nombre ="",
                                    [CallerFilePath] string Ruta="",
                                    [CallerLineNumber] int Linea=0) 
        {
            System.String MetodoActual = MethodBase.GetCurrentMethod().Name;

            System.String ClaseActual = MethodBase.GetCurrentMethod().DeclaringType.FullName; 

            Console.WriteLine(string.Format("Nombre del Metodo LLamador: {0}",Nombre));

            Console.WriteLine(string.Format("Nombre del Metodo Actual: {0}", MetodoActual));

            Console.WriteLine(string.Format("Nombre de la Clase Actual: {0}", ClaseActual));
            
            Console.WriteLine(string.Format("SEPARADOR: {0} ", "----------------"));
        }
        
    }
}

/*AGRADECIMIENTOS
 * http://nelson-venegas.blogspot.com/
 */
