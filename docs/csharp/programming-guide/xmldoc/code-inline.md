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
ms.openlocfilehash: 8471681f979fdd030490a5ecc306c4a4b9f624f9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276753"
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
  
 使用 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 編譯，可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
