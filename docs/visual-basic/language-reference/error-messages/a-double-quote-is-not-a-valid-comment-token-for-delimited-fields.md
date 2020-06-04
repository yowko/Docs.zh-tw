---
title: 在 EscapeQuote 設定為 True 的情況下，雙引號不是用於分隔欄位的有效註解語彙基元
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: a66d43d249a12ffa552073866f2e0a1e6d453608
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409932"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a><span data-ttu-id="49fae-102">在 EscapeQuote 設定為 True 的情況下，雙引號不是用於分隔欄位的有效註解語彙基元</span><span class="sxs-lookup"><span data-stu-id="49fae-102">A double quote is not a valid comment token for delimited fields where EscapeQuote is set to True</span></span>

<span data-ttu-id="49fae-103">引號已提供為 `TextFieldParser`的分隔符號，但 `EscapeQuotes` 設為 `True`。</span><span class="sxs-lookup"><span data-stu-id="49fae-103">A quotation mark has been supplied as the delimiter for the `TextFieldParser`, but `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="49fae-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="49fae-104">To correct this error</span></span>  
  
- <span data-ttu-id="49fae-105">將 `EscapeQuotes` 設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="49fae-105">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49fae-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49fae-106">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [<span data-ttu-id="49fae-107">作法：從逗號分隔文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="49fae-107">How to: Read From Comma-Delimited Text Files</span></span>](../../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
