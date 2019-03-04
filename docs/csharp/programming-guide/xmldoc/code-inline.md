---
title: <c> - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: e56df10eabc6a2d38bd049951b01c16808222255
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202297"
---
# <a name="c-c-programming-guide"></a>\<c> (C# 程式設計指南)
## <a name="syntax"></a>語法  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a>參數  
 `text`  
 您要指定為程式碼的文字。  
  
## <a name="remarks"></a>備註  
 \<c> 標記可讓您在一段描述中指出應該標記為程式碼的文字。 請使用 [\<code>](../../../csharp/programming-guide/xmldoc/code.md) 將多行指定為程式碼。  
  
 編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
