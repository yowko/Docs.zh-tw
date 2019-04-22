---
title: 反映 (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4dfd9391407fec4bd20ac4ae05162763e909d665
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841312"
---
# <a name="reflection-c"></a>反映 (C#)
反映提供的物件 (類型為 <xref:System.Type>) 可描述組件、模組和類型。 您可以使用反映來動態建立類型的執行個體、將類型繫結至現有的物件，或從現有的物件取得類型，並叫用其方法或存取其欄位及屬性。 如果您在程式碼中使用屬性，則反映可讓您存取它們。 如需詳細資訊，請參閱[屬性](../../../../docs/standard/attributes/index.md)。  
  
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
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 輸出為：  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  C# 關鍵字 `protected` 和 `internal` 在 IL 中沒有任何意義，而且不會用於反映 API 中。 IL 中的對應詞彙是「系列」和「組件」。 若要使用反映來識別 `internal` 方法，請使用 <xref:System.Reflection.MethodBase.IsAssembly%2A> 屬性。 若要識別 `protected internal` 方法，請使用 <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>。  
  
## <a name="reflection-overview"></a>反映概觀  
 反映在下列情況下十分有用：  
  
-   當您需要存取程式中繼資料中的屬性時。 如需詳細資訊，請參閱[擷取儲存於屬性中的資訊](../../../standard/attributes/retrieving-information-stored-in-attributes.md)。  
  
-   如需檢查和具現化組件中的類型。  
  
-   如需在執行階段建置新類型。 使用 <xref:System.Reflection.Emit> 中的類別。  
  
-   對於執行晚期繫結，存取在執行階段建立的類型上的方法。 請參閱[動態載入和使用類型](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)主題。  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊：  
  
-   [反映](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [檢視類型資訊](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [反映和泛用類型](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [擷取儲存於屬性中的資訊](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [Common Language Runtime 中的組件](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
