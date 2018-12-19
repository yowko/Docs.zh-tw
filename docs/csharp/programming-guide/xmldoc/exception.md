---
title: '&lt;例外狀況&gt; - C# 程式設計指南'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 09c2ce3d7c0c9b8c20d4a32aa1d4c84d4ead4fbf
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245531"
---
# <a name="ltexceptiongt-c-programming-guide"></a>&lt;例外狀況&gt; (C# 程式設計手冊)
## <a name="syntax"></a>語法  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>參數  
 cref = " `member`"  
 可從目前編譯環境取得之例外狀況的參考。 編譯器會檢查指定的例外狀況是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。 `member` 必須出現在雙引號內 (" ")。  
  
 如需如何建立泛型型別 cref 參考的詳細資訊，請參閱[\<請參閱>](../../../csharp/programming-guide/xmldoc/see.md)。  
  
 `description`  
 例外狀況的描述。  
  
## <a name="remarks"></a>備註  
 \<exception> 標記可讓您指定可以擲回的例外狀況。 這個標記可以套用至方法、屬性、事件和索引子的定義。  
  
 編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。  
  
 如需例外狀況處理的詳細資訊，請參閱[例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/index.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
