---
title: 當 EscapeQuotes 設定為 True 時，因為雙引號不是合法的分隔符號，所以無法讀取分隔的欄位。
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: 29682edb78b848897ac2999f2d84dc1a9c1a3367
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100350"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a><span data-ttu-id="58660-102">當 EscapeQuotes 設定為 True 時，因為雙引號不是合法的分隔符號，所以無法讀取分隔的欄位。</span><span class="sxs-lookup"><span data-stu-id="58660-102">Unable to read delimited fields because a double quote is not a legal delimiter when EscapeQuotes is set to True</span></span>

<span data-ttu-id="58660-103">`TextFieldParser` 無法從檔案讀取，因為引號 (") 已供做分隔符號且 `EscapeQuotes` 設為 `True`。</span><span class="sxs-lookup"><span data-stu-id="58660-103">The `TextFieldParser` cannot read from the file because a quotation mark (") has been supplied as the delimiter and `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="58660-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="58660-104">To correct this error</span></span>  
  
- <span data-ttu-id="58660-105">請設定 `EscapeQuotes` 為 `False`。</span><span class="sxs-lookup"><span data-stu-id="58660-105">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58660-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58660-106">See also</span></span>

- [<span data-ttu-id="58660-107">TextFieldParser.SetDelimiters 方法</span><span class="sxs-lookup"><span data-stu-id="58660-107">TextFieldParser.SetDelimiters Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [<span data-ttu-id="58660-108">TextFieldParser.Delimiters 屬性</span><span class="sxs-lookup"><span data-stu-id="58660-108">TextFieldParser.Delimiters Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [<span data-ttu-id="58660-109">作法：從逗號分隔文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="58660-109">How to: Read From Comma-Delimited Text Files</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="58660-110">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="58660-110">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
