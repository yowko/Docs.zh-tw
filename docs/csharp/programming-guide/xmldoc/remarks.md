---
title: <remarks> - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 3e6625c55a6f5c29fb55bff2eb87959f3237652e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975845"
---
# <a name="remarks-c-programming-guide"></a>\<remarks> (C# 程式設計指南)
## <a name="syntax"></a>語法  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>參數  
 `Description`  
 成員的描述。  
  
## <a name="remarks"></a>備註  
 \<remarks> 標記是用來新增類型的資訊，以補充使用 [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) 所指定的資訊。 這項資訊會顯示在 [物件瀏覽器] 視窗中。  
  
 使用 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 編譯，可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
