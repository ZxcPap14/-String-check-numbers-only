The work was completed by:

Денис Казанцев

Артем Николаев


#Library

	using System;
	using System.Collections.Generic;
	using System.Linq;
	using System.Text;
	using System.Threading.Tasks;
	namespace StringLibrary1
	{
	    //Концерт кишлака тут?
	    /// <summary>
	    /// Метод, который бы определял, что строка состоит только лишь из цифр
	    /// </summary>
	    /// <param name="textString">
	    /// </param>
	    /// <returns>
	    /// Метод возвращает true, если входная строка содержит только цифры
	    /// </returns>
	    public class StringClass
	    {
	        public static bool OnlyDigits(string testString)
	        {
	            testString = testString.Replace('.', ',');
	            double number;
	            bool result = double.TryParse(testString, out number);
	            if (!result)
	            {   
	                return false;
	            }
	            if (string.IsNullOrEmpty(testString))
	            { 
	                return false; 
	            }
	            if (testString.Length > 10 )
	            {
	                return false;
	            }
	            return true;
	        }
	    }
	} 
 #Tests
 
		using Microsoft.VisualStudio.TestTools.UnitTesting;
		using System;
		using StringLibrary1;
		namespace StringLibraryTest
		{
		    [TestClass]
		    public class CheckStringClassTest
		    {
		        /// <summary>
		        /// Только числа
		        /// </summary>
		        [TestMethod]
		        public void Only_Digits_ReturnTrue()
		        {
		            //Arrange
		            string testString = "1";
		            //Act
		            bool result= StringClass.OnlyDigits(testString);
		            //Assert
		            Assert.IsTrue(result);
		        }
		        [TestMethod]
		        public void scifroy_Digits_ReturnTrue()
		        {
		            //Arrange
		            string testString = "2.345";
		            //Act
		            bool result = StringClass.OnlyDigits(testString);
		            //Assert
		            Assert.IsTrue(result);
		        }
		        [TestMethod]
		        public void otric_Digits_ReturnTrue()
		        {
		            //Arrange
		            string testString = "-4,34";
		            //Act
		            bool result = StringClass.OnlyDigits(testString);
		            //Assert
		            Assert.IsTrue(result);
		        }
		        [TestMethod]
		        public void stochki_Digits_ReturnTrue()
		        {
		            //Arrange
		            string testString = ".6";
		            //Act
		            bool result = StringClass.OnlyDigits(testString);
		            //Assert
		            Assert.IsTrue(result);
		        }
		        [TestMethod]
		        public void zero_Digits_Returnfalse()
		        {
		            //Arrange
		            string testString = " ";
		            //Act
		            bool result = StringClass.OnlyDigits(testString);
		            //Assert
		            Assert.IsFalse(result);
		        }
		        [TestMethod]
		        public void many_Digits_Returnfalse()
		        {
		            //Arrange
		            string testString = "5555555555555";
		            //Act
		            bool result = StringClass.OnlyDigits(testString);
		            //Assert
		            Assert.IsFalse(result);
		        }
		        [TestMethod]
		        public void wrong_Digits_Returnfalse()
		        {
		            //Arrange
		            string testString = "-5555555555555";
		            //Act
		            bool result = StringClass.OnlyDigits(testString);
		            //Assert
		            Assert.IsFalse(result);
		        }
		        [TestMethod]
		        public void manyy_Digits_Returnfalse()
		        {
		            //Arrange
		            string testString = "jh#";
		            //Act
		            bool result = StringClass.OnlyDigits(testString);
		            //Assert
		            Assert.IsFalse(result);
		        }
		        [TestMethod]
		        public void centrmin_Digits_Returnfalse()
		        {
		            //Arrange
		            string testString = "4-4";
		            //Act
		            bool result = StringClass.OnlyDigits(testString);
		            //Assert
		            Assert.IsFalse(result);
		        }
		        [TestMethod]
		        public void TOCHKA_Digits_Returnfalse()
		        {
		            //Arrange
		            string testString = ".";
		            //Act
		            bool result = StringClass.OnlyDigits(testString);
		            //Assert
		            Assert.IsFalse(result);
		        }
		        [TestMethod]
		        public void bezcifer_Digits_Returnfalse()
		        {
		            //Arrange
		            string testString = "-.-";
		            //Act
		            bool result = StringClass.OnlyDigits(testString);
		            //Assert
		            Assert.IsFalse(result);
		        }
		    }
		}
