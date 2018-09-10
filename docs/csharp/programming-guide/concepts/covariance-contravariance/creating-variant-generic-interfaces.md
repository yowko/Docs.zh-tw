---
title: 建立 Variant 泛型介面 (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: d8e7e8a59aeff27531187e5171a76651440ffc4c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526903"
---
# <a name="creating-variant-generic-interfaces-c"></a>建立 Variant 泛型介面 (C#)
您可以在介面中將泛型型別參數宣告為 Covariant 或 Contravariant。 「共變數」允許介面方法具有比泛型型別參數衍生程度更大的傳回型別。 「反變數」允許介面具有比泛型參數所指定引數型別衍生程度更小的引數類型。 具有 Covariant 或 Contravariant 泛型型別參數的泛型介面稱為「變異」。  
  
> [!NOTE]
>  .NET Framework 4 引入了對於數個現有泛型介面的變異數支援。 .NET Framework 中的 Variant 介面清單，請參閱[泛型介面中的變異數 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)。  
  
## <a name="declaring-variant-generic-interfaces"></a>宣告 Variant 泛型介面  
 您可以使用泛型型別參數的 `in` 和 `out` 關鍵字宣告 Variant 泛型介面。  
  
> [!IMPORTANT]
>  C# 中的 `ref`、`in` 及 `out` 參數不可變動。 實值型別也不支援變異數。  
  
 您可以使用 `out` 關鍵字將泛型型別參數宣告為 Covariant 。 Covariant 類型必須滿足下列條件︰  
  
-   類型僅用為介面方法的傳回型別，不用為方法引數的類型。 這說明於下列範例中，其中 `R` 類型已宣告為 Covariant。  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        R GetSomething();  
        // The following statement generates a compiler error.  
        // void SetSometing(R sampleArg);  
  
    }  
    ```  
  
     這個規則只有一個例外。 如果您以 Contravariant 泛型委派作為方法參數，則可將類型用作委派的泛型型別參數。 以下範例的 `R` 類型說明這種情況： 如需詳細資訊，請參閱[委派中的變異數 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) 和[針對 Func 與 Action 泛型委派使用變異數](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        void DoSomething(Action<R> callback);  
    }  
    ```  
  
-   類型不會用作介面方法的泛型條件約束。 下列程式碼說明此情形。  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        // The following statement generates a compiler error  
        // because you can use only contravariant or invariant types  
        // in generic contstraints.  
        // void DoSomething<T>() where T : R;  
    }  
    ```  
  
 您可以使用 `in` 關鍵字將泛型型別參數宣告為 Contravariant 。 Contravariant 類型僅可用作方法引數的類型，而不能用作介面方法的傳回型別。 Contravariant 類型也用於泛型條件約束。 下列程式碼示範如何宣告 Contravariant 介面，並針對其中一個方法使用泛型條件約束。  
  
```csharp  
interface IContravariant<in A>  
{  
    void SetSomething(A sampleArg);  
    void DoSomething<T>() where T : A;  
    // The following statement generates a compiler error.  
    // A GetSomething();              
}  
```  
  
 也可以在相同介面中同時支援共變數和反變數，但是對於不同的型別參數，如下列程式碼範例所示。  
  
```csharp  
interface IVariant<out R, in A>  
{  
    R GetSomething();  
    void SetSomething(A sampleArg);  
    R GetSetSometings(A sampleArg);  
}  
```  
  
## <a name="implementing-variant-generic-interfaces"></a>實作 Variant 泛型介面  
 您可以使用用於非變異介面的相同語法，在類別中實作 Variant 泛型介面。 下列程式碼範例示範如何在泛型類別中實作 Covariant 介面。  
  
```csharp  
interface ICovariant<out R>  
{  
    R GetSomething();  
}  
class SampleImplementation<R> : ICovariant<R>  
{  
    public R GetSomething()  
    {  
        // Some code.  
        return default(R);  
    }  
}  
```  
  
 實作 Variant 介面的類別為非變異。 例如，試想下列程式碼。  
  
```csharp  
// The interface is covariant.  
ICovariant<Button> ibutton = new SampleImplementation<Button>();  
ICovariant<Object> iobj = ibutton;  
  
// The class is invariant.  
SampleImplementation<Button> button = new SampleImplementation<Button>();  
// The following statement generates a compiler error  
// because classes are invariant.  
// SampleImplementation<Object> obj = button;  
```  
  
## <a name="extending-variant-generic-interfaces"></a>擴充 Variant 泛型介面  
 當您擴充 Variant 泛型介面時，必須使用 `in` 和 `out` 關鍵字明確指定衍生的介面是否支援變異數。 編譯器不會從要擴充的介面推斷變異數。 例如，請參考下列介面。  
  
```csharp  
interface ICovariant<out T> { }  
interface IInvariant<T> : ICovariant<T> { }  
interface IExtCovariant<out T> : ICovariant<T> { }  
```  
  
 在 `IInvariant<T>` 介面中，`T` 泛型型別參數為非變異，而在 `IExtCovariant<out T>` 中，型別參數是 Covariant，雖然這兩個介面都擴充相同的介面。 相同的規則也套用至 Contravariant 泛型型別參數。  
  
 您可以建立介面，以便擴充 `T` 泛型型別參數為 Covariant 的介面，以及如果在擴充介面中， `T` 泛型型別參數為非變異的情況下，擴充其為 Contravariant 的介面。 下列程式碼範例說明此情形。  
  
```csharp  
interface ICovariant<out T> { }  
interface IContravariant<in T> { }  
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }  
```  
  
 不過，如果 `T` 泛型型別參數在一個介面中宣告為 Covariant，則無法在擴充的介面中將它宣告為 Contravariant，反之亦然。 下列程式碼範例說明此情形。  
  
```csharp  
interface ICovariant<out T> { }  
// The following statement generates a compiler error.  
// interface ICoContraVariant<in T> : ICovariant<T> { }  
```  
  
### <a name="avoiding-ambiguity"></a>避免語意模糊  
 當您實作 Variant 泛型介面時，變異數有時會導致語意模糊。 對此應該要設法避免。  
  
 例如，如果您在一個類別中，明確地實作相同 Variant 泛型介面與不同泛型型別參數，它可能會造成語意模糊。 在此情況下，編譯器不會產生錯誤，但未指定在執行階段將選擇哪個介面實作。 這可能會導致您的程式碼中有細微錯誤。 請參考下列程式碼範例。  
  
```csharp  
// Simple class hierarchy.  
class Animal { }  
class Cat : Animal { }  
class Dog : Animal { }  
  
// This class introduces ambiguity  
// because IEnumerable<out T> is covariant.  
class Pets : IEnumerable<Cat>, IEnumerable<Dog>  
{  
    IEnumerator<Cat> IEnumerable<Cat>.GetEnumerator()  
    {  
        Console.WriteLine("Cat");  
        // Some code.  
        return null;  
    }  
  
    IEnumerator IEnumerable.GetEnumerator()  
    {  
        // Some code.  
        return null;  
    }  
  
    IEnumerator<Dog> IEnumerable<Dog>.GetEnumerator()  
    {  
        Console.WriteLine("Dog");  
        // Some code.  
        return null;  
    }  
}  
class Program  
{  
    public static void Test()  
    {  
        IEnumerable<Animal> pets = new Pets();  
        pets.GetEnumerator();  
    }  
}  
```  
  
 在此範例中，並未指定 `pets.GetEnumerator` 方法如何在 `Cat` 和 `Dog` 之間選擇。 這可能會在程式碼中造成問題。  
  
## <a name="see-also"></a>請參閱

- [泛型介面中的變異數 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
- [針對 Func 與 Action 泛型委派使用變異數 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
