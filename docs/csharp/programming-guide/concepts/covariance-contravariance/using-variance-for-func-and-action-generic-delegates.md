---
title: "針對 Func 與 Action 泛型委派使用變異數 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 976057252a6cfa378008e9508145be7bc330fdc8
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>針對 Func 與 Action 泛型委派使用變異數 (C#)
下列範例示範如何在 `Func` 和 `Action` 泛型委派中使用共變數和反變數，以便在您的程式碼中重複使用方法並提供更多彈性。  
  
 如需共變數與反變數的詳細資訊，請參閱[委派中的變異數 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)。  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>使用具有 Covariant 型別參數的委派  
 下列範例說明在泛型 `Func` 委派中支援共變數的好處。 `FindByTitle` 方法使用 `String` 類型的參數，並傳回 `Employee` 類型的物件。 不過，您可以將此方法指派給 `Func<String, Person>` 委派，因為 `Employee` 會繼承 `Person`。  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>使用具有 Contravariant 型別參數的委派  
 下列範例說明在泛型 `Action` 委派中支援反變數的好處。 `AddToContacts` 方法使用 `Person` 類型的參數。 不過，您可以將此方法指派給 `Action<Employee>` 委派，因為 `Employee` 會繼承 `Person`。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [共變數和反變數 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/index.md)   
 [泛型](~/docs/standard/generics/index.md)

