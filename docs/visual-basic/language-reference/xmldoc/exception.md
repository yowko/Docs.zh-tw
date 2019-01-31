---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: b2475bd5eaeadc12e4c8c9b0fb77a2fa5cb88911
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283930"
---
# <a name="exception-visual-basic"></a>\<例外狀況 > (Visual Basic)
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
 這個範例會使用`<exception>`標記來描述例外狀況，`IntDivide`函式可能會擲回。  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a>另請參閱
- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)
