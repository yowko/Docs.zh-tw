---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 3a2452ec60a2182adfee365777d9824001ff006a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400120"
---
# <a name="exception-visual-basic"></a>\<exception> (Visual Basic)
指定可以擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a>參數  
 `member`  
 可從目前編譯環境取得之例外狀況的參考。 編譯器會檢查指定的例外狀況是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。 `member` 必須出現在雙引號內 (" ")。  
  
 `description`  
 描述。  
  
## <a name="remarks"></a>備註  
 使用 `<exception>` 標記來指定可以擲回的例外狀況。 此標記會套用到方法定義。  
  
 使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<exception>` 標記來描述函式可以擲回的例外狀況 `IntDivide` 。  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)
