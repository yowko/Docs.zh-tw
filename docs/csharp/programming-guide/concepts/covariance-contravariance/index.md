---
title: 共變數和反變數 (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 1d5a1de1825e585512f694a0cd72cee9b37cda36
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595281"
---
# <a name="covariance-and-contravariance-c"></a>共變數和反變數 (C#)
在 C# 中，共變數和反變數可讓您進行陣列類型、委派類型和泛型型別引數的隱含參考轉換。 共變數會保留指派相容性，而反變數則會將它反轉。  
  
 下列程式碼示範指派相容性、共變數和反變數之間的差異。  
  
```csharp  
// Assignment compatibility.   
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.   
object obj = str;  
  
// Covariance.   
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument   
// is assigned to an object instantiated with a less derived type argument.   
// Assignment compatibility is preserved.   
IEnumerable<object> objects = strings;  
  
// Contravariance.             
// Assume that the following method is in the class:   
// static void SetObject(object o) { }   
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument   
// is assigned to an object instantiated with a more derived type argument.   
// Assignment compatibility is reversed.   
Action<string> actString = actObject;  
```  
  
 陣列的共變數可將衍生程度較大類型的陣列，隱含轉換成衍生程度較小類型的陣列。 但這項作業不是型別安全的，如下列程式碼範例所示。  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 共變數和反變數的方法群組支援可讓您比對方法簽章和委派類型。 這可讓您指派方法給委派，不只是具有相符簽章的方法，也可以是會傳回衍生程度較大類型 (共變數) 的方法，或接受衍生程度比委派類型所指定更小類型 (反變數) 的方法。 如需詳細資訊，請參閱[委派中的變異數 (C#)](./variance-in-delegates.md) 和[在委派中使用變異數 (C#)](./using-variance-in-delegates.md)。  
  
 下列程式碼範例示範共變數和反變數的方法群組支援。  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 在 .NET Framework 4 或更新版本中，C# 支援泛型介面和委派中的共變數和反變數，並可讓您進行泛型型別參數的隱含轉換。 如需詳細資訊，請參閱[泛型介面中的變異數 (C#)](./variance-in-generic-interfaces.md) 和[委派中的變異數 (C#)](./variance-in-delegates.md)。  
  
 下列程式碼範例示範泛型介面的隱含參考轉換。  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 如果泛型介面或委派的泛型參數宣告為共變數或反變數，此泛型介面或委派稱為 *variant*。 C# 可讓您建立自己的 Variant 介面和委派。 如需詳細資訊，請參閱[建立 Variant 泛型介面 (C#)](./creating-variant-generic-interfaces.md) 和[委派中的差異 (C#)](./variance-in-delegates.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[泛型介面中的變異數 (C#)](./variance-in-generic-interfaces.md)|討論泛型介面中的共變性與逆變性，並提供.NET Framework 中的 Variant 泛型介面清單。|  
|[建立 Variant 泛型介面 (C#)](./creating-variant-generic-interfaces.md)|示範如何建立自訂 Variant 介面。|  
|[針對泛型集合使用介面中的差異 (C#)](./using-variance-in-interfaces-for-generic-collections.md)|示範 <xref:System.Collections.Generic.IEnumerable%601> 和 <xref:System.IComparable%601> 介面中的共變數和反變數支援如何協助您重複使用程式碼。|  
|[委派中的差異 (C#)](./variance-in-delegates.md)|討論泛型和非泛型委派中的共變性和反變數，並提供 .NET Framework 中的 Variant 泛型委派清單。|  
|[在委派中使用變異數 (C#)](./using-variance-in-delegates.md)|示範如何在非泛型委派中使用共變數和反變數支援，以比對方法簽章和委派類型。|  
|[針對 Func 與 Action 泛型委派使用變異數 (C#)](./using-variance-for-func-and-action-generic-delegates.md)|示範 `Func` 和 `Action` 委派中的共變數和反變數支援如何協助您重複使用程式碼。|
