---
title: "&lt;例外狀況&gt; (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bd859a09bfbe9f814bf57f0987fd49ded9ba7100
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
