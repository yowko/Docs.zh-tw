---
title: "委派中的差異 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c29d4ddbf5f1f9ae80535a8a97651b296f3c1fb3
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="variance-in-delegates-c"></a>委派中的差異 (C#)
.NET framework 3.5 推出差異支援，在 C# 中比對方法簽章和所有委派的委派型別。 這表示您可以指派給委派的不只是具有相符簽章的方法，也可以是會傳回更多衍生型別 (共變數) 的方法，或接受衍生型別 (反變數) 比委派型別指定少的參數的方法。 這包括泛型和非泛型委派。  
  
 例如，請考慮下列程式碼，有兩個類別和兩個委派︰泛型和非泛型。  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 當您建立 `SampleDelegate` 或 `SampleGenericDelegate<A, R>` 型別的委派時，您可以指派下列任一方法給這些委派。  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second first)  
{ return new First(); }  
  
// The return type is more derived.  
public static Second ASecondRSecond(Second second)  
{ return new Second(); }  
  
// The argument type is less derived.  
public static First AFirstRFirst(First first)  
{ return new First(); }  
  
// The return type is more derived   
// and the argument type is less derived.  
public static Second AFirstRSecond(First first)  
{ return new Second(); }  
```  
  
 下列程式碼範例會示範方法簽章與委派型別之間的隱含轉換。  
  
```csharp  
// Assigning a method with a matching signature   
// to a non-generic delegate. No conversion is necessary.  
SampleDelegate dNonGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type   
// and less derived argument type to a non-generic delegate.  
// The implicit conversion is used.  
SampleDelegate dNonGenericConversion = AFirstRSecond;  
  
// Assigning a method with a matching signature to a generic delegate.  
// No conversion is necessary.  
SampleGenericDelegate<Second, First> dGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type   
// and less derived argument type to a generic delegate.  
// The implicit conversion is used.  
SampleGenericDelegate<Second, First> dGenericConversion = AFirstRSecond;  
```  
  
 如需更多範例，請參閱[在委派中使用差異 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) 和[針對 Func 與 Action 泛型委派使用差異 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。  
  
## <a name="variance-in-generic-type-parameters"></a>泛型型別參數中的差異  
 在 .NET Framework 4 或更新版本中可以啟用委派之間的隱含轉換，因此具有泛型型別參數所指定的不同型別的泛型委派可互相指派，如果型別繼承自彼此，如差異所要求。  
  
 若要啟用隱含轉換，您必須使用 `in` 或 `out` 關鍵字，明確宣告委派中的泛型參數為 Covariant 或 Contravariant。  
  
 下列程式碼範例示範如何建立具有 Covariant 泛型型別參數的委派。  
  
```csharp  
// Type T is declared covariant by using the out keyword.  
public delegate T SampleGenericDelegate <out T>();  
  
public static void Test()  
{  
    SampleGenericDelegate <String> dString = () => " ";  
  
    // You can assign delegates to each other,  
    // because the type T is declared covariant.  
    SampleGenericDelegate <Object> dObject = dString;             
}  
```  
  
 如果您使用唯一的差異支援來比對方法簽章與委派型別，請不要使用 `in` 和 `out` 關鍵字，因為您會發現，有時候您會使用相同的 lambda 運算式或方法具現化委派，但無法將一個委派指派給另一個。  
  
 在下列程式碼範例中，`SampleGenericDelegate<String>` 無法明確地轉換成 `SampleGenericDelegate<Object>`，雖然 `String` 繼承 `Object`。 您可以使用 `out` 關鍵字標記泛型參數 `T`，修正這個問題。  
  
```csharp  
public delegate T SampleGenericDelegate<T>();  
  
public static void Test()  
{  
    SampleGenericDelegate<String> dString = () => " ";  
  
    // You can assign the dObject delegate  
    // to the same lambda expression as dString delegate  
    // because of the variance support for   
    // matching method signatures with delegate types.  
    SampleGenericDelegate<Object> dObject = () => " ";  
  
    // The following statement generates a compiler error  
    // because the generic type T is not marked as covariant.  
    // SampleGenericDelegate <Object> dObject = dString;  
  
}  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>.NET Framework 中具有 Variant 型別參數的泛型委派  
 .NET Framework 4 推出差異支援，適用於數個現有泛型委派中的泛型型別參數：  
  
-   <xref:System> 命名空間中的 `Action` 委派，例如 <xref:System.Action%601> 和 <xref:System.Action%602>  
  
-   <xref:System> 命名空間中的 `Func` 委派，例如 <xref:System.Func%601> 和 <xref:System.Func%602>  
  
-   <xref:System.Predicate%601> 委派  
  
-   <xref:System.Comparison%601> 委派  
  
-   <xref:System.Converter%602> 委派  
  
 如需詳細資訊及更多範例，請參閱[針對 Func 與 Action 泛型委派使用差異 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>宣告泛型委派中的 Variant 型別參數  
 如果泛型委派具有 Covariant 或 Contravariant 泛型型別參數，它可以稱之為「Variant 泛型委派」。  
  
 您可以使用 `out` 關鍵字將泛型委派中的泛型型別參數宣告為 Covariant。 Covariant 型別僅可用為方法傳回型別，不能用為方法引數的型別。 以下程式碼範例會示範如何宣告 Covariant 泛型委派。  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 您可以使用 `in` 關鍵字將泛型委派中的泛型型別參數宣告為 Contravariant。 Contravariant 型別僅可用為方法引數的型別，不能用為方法傳回型別。 以下程式碼範例會示範如何宣告 Contravariant 泛型委派。  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  C# 中的 `ref`、`in` 和 `out` 參數不可標示為可變動。  
  
 您也可以支援相同委派中不同型別參數的差異和共變數。 這在下列範例中顯示。  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>具現化及叫用 Variant 泛型委派  
 您可以具現化及叫用 Variant 委派，一如您具現化及叫用非變異委派。 在下例中，委派是由 lambda 運算式具現化。  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>結合 Variant 泛型委派  
 您不應該組合 Variant 委派。 <xref:System.Delegate.Combine%2A> 方法不支援 Variant 委派轉換，且委派的類型必須完全一致。 當您使用 <xref:System.Delegate.Combine%2A> 方法或使用 `+` 運算子合併委派時，這會導致執行階段例外狀況，如下列程式碼範例所示。  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>實值型別和參考型別的泛型型別參數中的差異  
 僅參考型別支援泛型型別參數的差異。 例如，因為整數是實值型別，所以 `DVariant<int>` 無法以隱含方式轉換成`DVariant<Object>` 或 `DVariant<long>`。  
  
 下例示範實值型別不支援的泛型型別參數的差異。  
  
```csharp  
// The type T is covariant.  
public delegate T DVariant<out T>();  
  
// The type T is invariant.  
public delegate T DInvariant<T>();  
  
public static void Test()  
{  
    int i = 0;  
    DInvariant<int> dInt = () => i;  
    DVariant<int> dVariantInt = () => i;  
  
    // All of the following statements generate a compiler error  
    // because type variance in generic parameters is not supported  
    // for value types, even if generic type parameters are declared variant.  
    // DInvariant<Object> dObject = dInt;  
    // DInvariant<long> dLong = dInt;  
    // DVariant<Object> dVariantObject = dVariantInt;  
    // DVariant<long> dVariantLong = dVariantInt;              
}  
```  
  
## <a name="see-also"></a>請參閱  
 [泛型](~/docs/standard/generics/index.md)  
 [針對 Func 與 Action 泛型委派使用變異數 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)  
 [如何：組合委派 (多點傳送委派)](../../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
