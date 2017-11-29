---
title: "&lt;例外狀況&gt;(Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d718a7c2213a61f7f60ed80a04f9bd03f6c770a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltexceptiongt-visual-basic"></a>&lt;例外狀況&gt;(Visual Basic)
指定可以擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>參數  
 `member`  
 可從目前編譯環境取得之例外狀況的參考。 編譯器會檢查指定的例外狀況是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。 `member` 必須出現在雙引號內 (" ")。  
  
 `description`  
 描述。  
  
## <a name="remarks"></a>備註  
 使用`<exception>`標記來指定可以擲回的例外狀況。 此標記會套用到方法定義。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<exception>`標記來描述例外狀況，`IntDivide`函式可能擲回。  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
