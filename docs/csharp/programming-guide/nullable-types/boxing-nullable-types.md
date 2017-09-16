---
title: "Box 處理可為 Null 的類型 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5ce063a70ced98fd8b99b4b46d704e08ddc96e10
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="boxing-nullable-types-c-programming-guide"></a>Box 處理可為 Null 的類型 (C# 程式設計手冊)
如為非 Null 的物件，以可為 Null 的型別為基礎的物件僅能以 boxing 處理。 如果 <xref:System.Nullable%601.HasValue%2A> 是 `false`，則物件參考會指派給 `null` 而不是 boxing。 例如：  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 如果為非 Null 的物件 - 如果 <xref:System.Nullable%601.HasValue%2A> 是 `true` - 則發生 boxing，但只有可為 Null 物件依據的基礎類型會經過 boxing 處理。 以 boxing 處理非 Null 的可為 Null 的實值型別，會以 boxing 處理實值型別本身，不會處理包裝實值型別的 <xref:System.Nullable%601?displayProperty=fullName>。 例如：  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 兩個經過 boxing 處理的物件，和經過 boxing 處理的不可為 Null 的型別所建立的物件相同。 而且，就像經過 boxing 處理的不可為 Null 的型別，它們可以取消 boxing 處理成為可為 Null 的型別，如下例所示︰  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a>備註  
 經過 boxing 處理後，可為 Null 之型別的行為提供兩個優點︰  
  
1.  可為 Null 的物件及其經過 boxing 處理過的對應項目，可進行 Null 測試︰  
  
    ```csharp  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  經過 boxing 處理的可為 Null 的型別完全支援基礎類型的功能︰  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)   
 [可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)   
 [如何：識別可為 Null 的型別](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)

