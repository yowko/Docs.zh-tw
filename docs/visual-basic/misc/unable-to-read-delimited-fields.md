---
title: 當 EscapeQuotes 設定為 True 時，因為雙引號不是合法的分隔符號，所以無法讀取分隔的欄位。
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: cd2dd4226296ecd210a1e72a7b7fb593874b0008
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398470"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a><span data-ttu-id="c3069-102">當 EscapeQuotes 設定為 True 時，因為雙引號不是合法的分隔符號，所以無法讀取分隔的欄位。</span><span class="sxs-lookup"><span data-stu-id="c3069-102">Unable to read delimited fields because a double quote is not a legal delimiter when EscapeQuotes is set to True</span></span>
<span data-ttu-id="c3069-103">`TextFieldParser` 無法從檔案讀取，因為引號 (") 已供做分隔符號且 `EscapeQuotes` 設為 `True`。</span><span class="sxs-lookup"><span data-stu-id="c3069-103">The `TextFieldParser` cannot read from the file because a quotation mark (") has been supplied as the delimiter and `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c3069-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c3069-104">To correct this error</span></span>  
  
- <span data-ttu-id="c3069-105">將 `EscapeQuotes` 設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="c3069-105">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3069-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3069-106">See also</span></span>

- [<span data-ttu-id="c3069-107">TextFieldParser.SetDelimiters 方法</span><span class="sxs-lookup"><span data-stu-id="c3069-107">TextFieldParser.SetDelimiters Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [<span data-ttu-id="c3069-108">TextFieldParser.Delimiters 屬性</span><span class="sxs-lookup"><span data-stu-id="c3069-108">TextFieldParser.Delimiters Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [<span data-ttu-id="c3069-109">作法：從逗號分隔文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="c3069-109">How to: Read From Comma-Delimited Text Files</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="c3069-110">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="c3069-110">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
