---
title: '&lt;c&gt; (C# 程式設計手冊)'
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
ms.openlocfilehash: 2220c42485674eaa4ba4e3b2dfb03865ad8013cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508143"
---
# <a name="ltcgt-c-programming-guide"></a>&lt;c&gt; (C# 程式設計手冊)
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
 [!code-csharp[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
