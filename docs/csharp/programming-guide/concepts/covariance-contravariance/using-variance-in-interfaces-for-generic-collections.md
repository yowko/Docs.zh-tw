---
title: 針對泛型集合使用介面中的變異數 (C#)
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: 7f1c44ecc831a7eb35541a432bc776c512bd10a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340459"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a>針對泛型集合使用介面中的變異數 (C#)
Covariant 介面允許其方法傳回與介面中指定的類型相比，其衍生程度較大的類型。 Contravariant 介面允許其方法接受與介面中指定的參數相比，其類型衍生程度較小的參數。  
  
 在 .NET Framework 4 中，有數個現有介面已變成 Covariant 和 Contravariant。 這些結構包括 <xref:System.Collections.Generic.IEnumerable%601> 及 <xref:System.IComparable%601>。 因此，您可以針對衍生類型的集合，重複使用搭配基底類型之泛型集合運作的方法。  
  
 如需 .NET Framework 中的 Variant 介面清單，請參閱[泛型介面中的變異數 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)。  
  
## <a name="converting-generic-collections"></a>轉換泛型集合  
 下列範例說明在 <xref:System.Collections.Generic.IEnumerable%601> 介面中支援共變數的好處。 `PrintFullName` 方法接受 `IEnumerable<Person>` 類型的集合作為參數。 不過，您可以重複用於 `IEnumerable<Employee>` 類型的集合，因為 `Employee` 會繼承 `Person`。  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
class Program  
{  
    // The method has a parameter of the IEnumerable<Person> type.  
    public static void PrintFullName(IEnumerable<Person> persons)  
    {  
        foreach (Person person in persons)  
        {  
            Console.WriteLine("Name: {0} {1}",  
            person.FirstName, person.LastName);  
        }  
    }  
  
    public static void Test()  
    {  
        IEnumerable<Employee> employees = new List<Employee>();  
  
        // You can pass IEnumerable<Employee>,   
        // although the method expects IEnumerable<Person>.  
  
        PrintFullName(employees);  
  
    }  
}  
```  
  
## <a name="comparing-generic-collections"></a>比較泛型集合  
 下列範例說明在 <xref:System.Collections.Generic.IComparer%601> 介面中支援反變數的好處。 `PersonComparer` 類別會實作 `IComparer<Person>` 介面。 不過，您可以重複使用此類別來比較一連串類型為 `Employee` 的物件，因為 `Employee` 會繼承 `Person`。  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
// The custom comparer for the Person type  
// with standard implementations of Equals()  
// and GetHashCode() methods.  
class PersonComparer : IEqualityComparer<Person>  
{  
    public bool Equals(Person x, Person y)  
    {              
        if (Object.ReferenceEquals(x, y)) return true;  
        if (Object.ReferenceEquals(x, null) ||  
            Object.ReferenceEquals(y, null))  
            return false;              
        return x.FirstName == y.FirstName && x.LastName == y.LastName;  
    }  
    public int GetHashCode(Person person)  
    {  
        if (Object.ReferenceEquals(person, null)) return 0;  
        int hashFirstName = person.FirstName == null  
            ? 0 : person.FirstName.GetHashCode();  
        int hashLastName = person.LastName.GetHashCode();  
        return hashFirstName ^ hashLastName;  
    }  
}  
  
class Program  
{  
  
    public static void Test()  
    {  
        List<Employee> employees = new List<Employee> {  
               new Employee() {FirstName = "Michael", LastName = "Alexander"},  
               new Employee() {FirstName = "Jeff", LastName = "Price"}  
            };  
  
        // You can pass PersonComparer,   
        // which implements IEqualityComparer<Person>,  
        // although the method expects IEqualityComparer<Employee>.  
  
        IEnumerable<Employee> noduplicates =  
            employees.Distinct<Employee>(new PersonComparer());  
  
        foreach (var employee in noduplicates)  
            Console.WriteLine(employee.FirstName + " " + employee.LastName);  
    }  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [泛型介面中的變異數 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
