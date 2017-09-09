---
title: "反映 (C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ab40ab2258703670576084eccf7fd7e1b113d08d
ms.lasthandoff: 03/13/2017

---
# <a name="reflection-c"></a>反映 (C#)
反映提供可描述組件、模組和類型的物件 (類型為 <xref:System.Type>)。 您可以使用反映來動態建立類型的執行個體、將類型繫結至現有的物件，或從現有的物件取得類型，並叫用其方法或存取其欄位及屬性。 如果您在程式碼中使用屬性，則反映可讓您存取它們。 如需詳細資訊，請參閱[屬性](https://msdn.microsoft.com/library/5x6cd29c)。  
  
 以下簡單反映範例使用 `Object` 基底類別的所有類型所繼承的靜態方法 `GetType` 來取得變數的類型︰  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 輸出為：  
  
 `System.Int32`  
  
 下列範例使用反映以取得所載入組件的完整名稱。  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 輸出為：  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  C# 關鍵字 `protected` 和 `internal` 在 IL 中沒有任何意義，而且不會用於反映 API 中。 IL 中的對應詞彙是「系列」**和「組件」**。 若要使用反映來識別 `internal` 方法，請使用 <xref:System.Reflection.MethodBase.IsAssembly%2A> 屬性。 若要識別 `protected internal` 方法，請使用 <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>。  
  
## <a name="reflection-overview"></a>反映概觀  
 反映在下列情況下十分有用：  
  
-   當您需要存取程式中繼資料中的屬性時。 如需詳細資訊，請參閱[擷取儲存於屬性中的資訊](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)。  
  
-   如需檢查和具現化組件中的類型。  
  
-   如需在執行階段建置新類型。 使用 <xref:System.Reflection.Emit> 中的類別。  
  
-   對於執行晚期繫結，存取在執行階段建立的類型上的方法。 請參閱[動態載入和使用類型](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc)主題。  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊：  
  
-   [反映](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775)  
  
-   [檢視類型資訊](http://msdn.microsoft.com/library/7e7303a9-4064-4738-b4e7-b75974ed70d2)  
  
-   [反映和泛用類型](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)  
  
-   <xref:System.Reflection.Emit>  
  
-   [擷取儲存於屬性中的資訊](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [Common Language Runtime 中的組件](https://msdn.microsoft.com/library/k3677y81)
