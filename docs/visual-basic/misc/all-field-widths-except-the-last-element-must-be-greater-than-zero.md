---
title: 除了最後項目以外的所有欄位寬度都必須大於零
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_FieldWidthsMustPositive
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
ms.openlocfilehash: 806dcef7b7a29afa8804a581659023c817662434
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940656"
---
# <a name="all-field-widths-except-the-last-element-must-be-greater-than-zero"></a><span data-ttu-id="821c6-102">除了最後項目以外的所有欄位寬度都必須大於零</span><span class="sxs-lookup"><span data-stu-id="821c6-102">All field widths, except the last element, must be greater than zero</span></span>
<span data-ttu-id="821c6-103">除了最後項目以外的所有欄位寬度都必須大於零。</span><span class="sxs-lookup"><span data-stu-id="821c6-103">All field widths, except the last element, must be greater than zero.</span></span> <span data-ttu-id="821c6-104">最後項目的欄位寬度小於或等於零，表示最後欄位是可變長度。</span><span class="sxs-lookup"><span data-stu-id="821c6-104">A field width less than or equal to zero in the last element indicates the last field is of variable length.</span></span>  
  
 <span data-ttu-id="821c6-105">作業失敗，因為除了最後項目以外的欄位寬度都設定為等於或小於零。</span><span class="sxs-lookup"><span data-stu-id="821c6-105">The operation has failed because a field width other than the last element is set to zero or less.</span></span> <span data-ttu-id="821c6-106">小於或等於零的欄位寬度可以用作最後項目，表示最後欄位是可變長度，但不能用作任何其他項目。</span><span class="sxs-lookup"><span data-stu-id="821c6-106">A field width less than or equal to zero can be used as the last element to indicate that the last field is of variable length, but it cannot be used as any other element.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="821c6-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="821c6-107">To correct this error</span></span>  
  
- <span data-ttu-id="821c6-108">將欄位寬度設定為正確的長度。</span><span class="sxs-lookup"><span data-stu-id="821c6-108">Set the field width to the correct length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="821c6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="821c6-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths>
- [<span data-ttu-id="821c6-110">如何：從固定寬度的文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="821c6-110">How to: Read From Fixed-width Text Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="821c6-111">TextFieldParser 物件</span><span class="sxs-lookup"><span data-stu-id="821c6-111">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
