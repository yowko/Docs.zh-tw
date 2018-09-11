---
title: 針對 Func 與 Action 泛型委派使用變異數 (C#)
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: 903926bc86b1b96cea25b91314e35ed4771bbcb9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44222223"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="7fac7-102">針對 Func 與 Action 泛型委派使用變異數 (C#)</span><span class="sxs-lookup"><span data-stu-id="7fac7-102">Using Variance for Func and Action Generic Delegates (C#)</span></span>
<span data-ttu-id="7fac7-103">下列範例示範如何在 `Func` 和 `Action` 泛型委派中使用共變數和反變數，以便在您的程式碼中重複使用方法並提供更多彈性。</span><span class="sxs-lookup"><span data-stu-id="7fac7-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="7fac7-104">如需共變數與反變數的詳細資訊，請參閱[委派中的變異數 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="7fac7-104">For more information about covariance and contravariance, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="7fac7-105">使用具有 Covariant 型別參數的委派</span><span class="sxs-lookup"><span data-stu-id="7fac7-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="7fac7-106">下列範例說明在泛型 `Func` 委派中支援共變數的好處。</span><span class="sxs-lookup"><span data-stu-id="7fac7-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="7fac7-107">`FindByTitle` 方法使用 `String` 類型的參數，並傳回 `Employee` 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="7fac7-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="7fac7-108">不過，您可以將此方法指派給 `Func<String, Person>` 委派，因為 `Employee` 會繼承 `Person`。</span><span class="sxs-lookup"><span data-stu-id="7fac7-108">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static Employee FindByTitle(String title)  
    {  
        // This is a stub for a method that returns  
        // an employee that has the specified title.  
        return new Employee();  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Func<String, Employee> findEmployee = FindByTitle;  
  
        // The delegate expects a method to return Person,  
        // but you can assign it a method that returns Employee.  
        Func<String, Person> findPerson = FindByTitle;  
  
        // You can also assign a delegate   
        // that returns a more derived type   
        // to a delegate that returns a less derived type.  
        findPerson = findEmployee;  
  
    }  
}  
```  
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="7fac7-109">使用具有 Contravariant 型別參數的委派</span><span class="sxs-lookup"><span data-stu-id="7fac7-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="7fac7-110">下列範例說明在泛型 `Action` 委派中支援反變數的好處。</span><span class="sxs-lookup"><span data-stu-id="7fac7-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="7fac7-111">`AddToContacts` 方法使用 `Person` 類型的參數。</span><span class="sxs-lookup"><span data-stu-id="7fac7-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="7fac7-112">不過，您可以將此方法指派給 `Action<Employee>` 委派，因為 `Employee` 會繼承 `Person`。</span><span class="sxs-lookup"><span data-stu-id="7fac7-112">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
```csharp  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static void AddToContacts(Person person)  
    {  
        // This method adds a Person object  
        // to a contact list.  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Action<Person> addPersonToContacts = AddToContacts;  
  
        // The Action delegate expects   
        // a method that has an Employee parameter,  
        // but you can assign it a method that has a Person parameter  
        // because Employee derives from Person.  
        Action<Employee> addEmployeeToContacts = AddToContacts;  
  
        // You can also assign a delegate   
        // that accepts a less derived parameter to a delegate   
        // that accepts a more derived parameter.  
        addEmployeeToContacts = addPersonToContacts;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7fac7-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="7fac7-113">See Also</span></span>

- [<span data-ttu-id="7fac7-114">共變數和反變數 (C#)</span><span class="sxs-lookup"><span data-stu-id="7fac7-114">Covariance and Contravariance (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/index.md)  
- [<span data-ttu-id="7fac7-115">泛型</span><span class="sxs-lookup"><span data-stu-id="7fac7-115">Generics</span></span>](~/docs/standard/generics/index.md)
