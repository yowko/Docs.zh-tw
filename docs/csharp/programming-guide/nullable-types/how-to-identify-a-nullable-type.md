---
title: 如何：識別可為 Null 的類型 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: f3ac4ebd77fc92a133eb326919d5ba55264ced97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333179"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>如何：識別可為 Null 的類型 (C# 程式設計手冊)
您可以使用 C# [typeof](../../../csharp/language-reference/keywords/typeof.md) 運算子來建立代表可為 Null 類型的 <xref:System.Type> 物件：  
  
```  
System.Type type = typeof(int?);  
```  
  
 您也可以使用 <xref:System.Reflection> 命名空間的類別和方法，產生代表可為 Null 類型的 <xref:System.Type> 物件。 不過，如果您使用 <xref:System.Object.GetType%2A> 方法或 `is` 運算子嘗試在執行階段從可為 Null 的變數取得類型資訊，結果會是代表基礎類型的 <xref:System.Type>，不是可為 Null 的類型本身。  
  
 當類型以隱含方式轉換成 <xref:System.Object> 時，在可為 Null 的類型上呼叫 `GetType`，會導致執行 boxing 作業。 因此 <xref:System.Object.GetType%2A> 一律會傳回表示基礎類型的 <xref:System.Type> 物件，不是可為 Null 的類型。  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 C# [是](../../../csharp/language-reference/keywords/is.md)運算子，也會在可為 Null 的基礎類型上運作。 因此，您無法使用 `is` 判斷變數是否是可為 Null 的類型。 下例顯示 `is` 運算子將 Nullable\<int> 變數當做 int。  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## <a name="example"></a>範例  
 使用下列程式碼判斷 <xref:System.Type> 物件是否代表可為 Null 的類型。 請記住，如果 `Type` 物件是從對 <xref:System.Object.GetType%2A> 的呼叫所傳回，這段程式碼一律會傳回 false，如本主題前文所述。  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## <a name="see-also"></a>請參閱  
 [可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)  
 [對可為 Null 的型別進行 boxing](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)
