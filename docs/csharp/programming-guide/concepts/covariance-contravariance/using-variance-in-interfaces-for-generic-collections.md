---
title: "針對泛型集合使用介面中的變異數 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: be04b5c07eaf80058153a6e3866d405f48cea4e4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="703b2-102">針對泛型集合使用介面中的變異數 (C#)</span><span class="sxs-lookup"><span data-stu-id="703b2-102">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="703b2-103">Covariant 介面允許其方法傳回與介面中指定的類型相比，其衍生程度較大的類型。</span><span class="sxs-lookup"><span data-stu-id="703b2-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="703b2-104">Contravariant 介面允許其方法接受與介面中指定的參數相比，其類型衍生程度較小的參數。</span><span class="sxs-lookup"><span data-stu-id="703b2-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="703b2-105">在 .NET Framework 4 中，有數個現有介面已變成 Covariant 和 Contravariant。</span><span class="sxs-lookup"><span data-stu-id="703b2-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="703b2-106">這些結構包括 <xref:System.Collections.Generic.IEnumerable%601> 及 <xref:System.IComparable%601>。</span><span class="sxs-lookup"><span data-stu-id="703b2-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="703b2-107">因此，您可以針對衍生類型的集合，重複使用搭配基底類型之泛型集合運作的方法。</span><span class="sxs-lookup"><span data-stu-id="703b2-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="703b2-108">如需 .NET Framework 中的 Variant 介面清單，請參閱[泛型介面中的變異數 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="703b2-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="703b2-109">轉換泛型集合</span><span class="sxs-lookup"><span data-stu-id="703b2-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="703b2-110">下列範例說明在 <xref:System.Collections.Generic.IEnumerable%601> 介面中支援共變數的好處。</span><span class="sxs-lookup"><span data-stu-id="703b2-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="703b2-111">`PrintFullName` 方法接受 `IEnumerable<Person>` 類型的集合作為參數。</span><span class="sxs-lookup"><span data-stu-id="703b2-111">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="703b2-112">不過，您可以重複用於 `IEnumerable<Employee>` 類型的集合，因為 `Employee` 會繼承 `Person`。</span><span class="sxs-lookup"><span data-stu-id="703b2-112">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="703b2-113">比較泛型集合</span><span class="sxs-lookup"><span data-stu-id="703b2-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="703b2-114">下列範例說明在 <xref:System.Collections.Generic.IComparer%601> 介面中支援反變數的好處。</span><span class="sxs-lookup"><span data-stu-id="703b2-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="703b2-115">`PersonComparer` 類別會實作 `IComparer<Person>` 介面。</span><span class="sxs-lookup"><span data-stu-id="703b2-115">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="703b2-116">不過，您可以重複使用此類別來比較一連串類型為 `Employee` 的物件，因為 `Employee` 會繼承 `Person`。</span><span class="sxs-lookup"><span data-stu-id="703b2-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="703b2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="703b2-117">See Also</span></span>  
 [<span data-ttu-id="703b2-118">泛型介面中的變異數 (C#)</span><span class="sxs-lookup"><span data-stu-id="703b2-118">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
