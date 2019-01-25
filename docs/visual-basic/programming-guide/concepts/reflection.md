---
title: 反映 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 59910edda8e2dfc4ec8e697b1d5b9a0f47ff9dbe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690107"
---
# <a name="reflection-visual-basic"></a>反映 (Visual Basic)
反映提供的物件 (類型為 <xref:System.Type>) 可描述組件、模組和類型。 您可以使用反映來動態建立類型的執行個體、將類型繫結至現有的物件，或從現有的物件取得類型，並叫用其方法或存取其欄位及屬性。 如果您在程式碼中使用屬性，則反映可讓您存取它們。 如需詳細資訊，請參閱[屬性](../../../standard/attributes/index.md)。  
  
 以下簡單反映範例使用 `Object` 基底類別的所有類型所繼承的靜態方法 `GetType` 來取得變數的類型︰  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 輸出為：  
  
 `System.Int32`  
  
 下列範例使用反映以取得所載入組件的完整名稱。  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 輸出為：  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
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
- [Visual Basic 程式設計手冊](../../../visual-basic/programming-guide/index.md)
- [Common Language Runtime 中的組件](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
