---
title: 結構 (C# 程式設計手冊)
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 27d4b0d7edf1b5e89e84ac1df5783d68ebb4efe0
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259480"
---
# <a name="structs-c-programming-guide"></a>結構 (C# 程式設計手冊)

您可以使用 [struct](../../language-reference/keywords/struct.md) 關鍵字來定義結構，例如：  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
Struct 大部分與 class 共用相同語法。 結構的名稱必須是有效的 C# [識別碼名稱](../inside-a-program/identifier-names.md)。 Struct 的限制在下列各方面比 class 多：  
  
- 在結構宣告內，除非欄位宣告為常數或靜態，否則無法初始化欄位。  
- 結構無法宣告預設建構函式 (不含參數的建構函式) 或完成項。  
- 指派時會複製結構。 將結構指派給新的變數時，會複製所有資料，而且對新複本進行的任何修改都不會變更原始複本的資料。 使用 `Dictionary<string, myStruct>` 這類實值型別的集合時，請務必記住。  
- Struct 是實值型別，不像 class 是參考型別。  
- 不同於類別，結構不需要使用 `new` 運算子就能具現化。  
- 結構可以宣告具有參數的建構函式。 
- 結構無法繼承自另一個結構或類別，而且不能作為類別的基底。 所有結構都直接繼承自 <xref:System.ValueType>，該項則繼承自 <xref:System.Object>。  
- 結構可以實作介面。  
- 結構可用作可為 Null 的型別，並可指派 Null 值。  
  
## <a name="related-sections"></a>相關章節  

如需詳細資訊：  
  
- [使用結構](using-structs.md)
- [建構函式](constructors.md)
- [可為 Null 的型別](../nullable-types/index.md)
- [如何：了解將結構和類別參考傳遞給方法之間的差異](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [如何：在結構之間實作使用者定義的轉換](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [類別和結構](index.md)
- [類別](classes.md)
- [識別碼名稱](../inside-a-program/identifier-names.md)
