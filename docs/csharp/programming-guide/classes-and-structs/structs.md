---
title: 結構 - C# 程式設計手冊
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 5150ff2d6edde0ac91bc6548fd499b76af614007
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705414"
---
# <a name="structs-c-programming-guide"></a>結構 (C# 程式設計手冊)

您可以使用 [struct](../../language-reference/keywords/struct.md) 關鍵字來定義結構，例如：  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
Struct 大部分與 class 共用相同語法。 結構的名稱必須是有效的 C# [識別碼名稱](../inside-a-program/identifier-names.md)。 Struct 的限制在下列各方面比 class 多：  
  
- 在結構宣告內，除非欄位宣告為常數或靜態，否則無法初始化欄位。  
- 結構無法宣告無參數建構函式 (不含參數的建構函式) 或完成項。  
- 指派時會複製結構。 將結構指派給新的變數時，會複製所有資料，而且對新複本進行的任何修改都不會變更原始複本的資料。 使用 `Dictionary<string, myStruct>` 這類實值型別的集合時，請務必記住。  
- Struct 是實值型別，不像 class 是參考型別。  
- 不同於類別，結構不需要使用 `new` 運算子就能具現化。  
- 結構可以宣告具有參數的建構函式。
- 結構無法繼承自另一個結構或類別，而且不能作為類別的基底。 所有結構都直接繼承自 <xref:System.ValueType>，該項則繼承自 <xref:System.Object>。  
- 結構可以實作介面。
- 無法 `null`結構，而且除非將變數宣告為可為 null 的實值型別，否則無法將結構變數指派 `null`。
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../index.md)
- [類別和結構](index.md)
- [類別](classes.md)
- [可為 Null 的實值型別](../../language-reference/builtin-types/nullable-value-types.md)
- [識別碼名稱](../inside-a-program/identifier-names.md)
- [使用結構](using-structs.md)
- [如何瞭解傳遞結構和將類別參考傳遞給方法之間的差異](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
