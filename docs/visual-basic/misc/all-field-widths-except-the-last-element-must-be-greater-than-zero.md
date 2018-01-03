---
title: "除了最後項目以外的所有欄位寬度都必須大於零"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrTextFieldParser_FieldWidthsMustPositive
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b348494c0a3103641d29998218b546de0d432e2a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="all-field-widths-except-the-last-element-must-be-greater-than-zero"></a><span data-ttu-id="fb0bc-102">除了最後項目以外的所有欄位寬度都必須大於零</span><span class="sxs-lookup"><span data-stu-id="fb0bc-102">All field widths, except the last element, must be greater than zero</span></span>
<span data-ttu-id="fb0bc-103">除了最後項目以外的所有欄位寬度都必須大於零。</span><span class="sxs-lookup"><span data-stu-id="fb0bc-103">All field widths, except the last element, must be greater than zero.</span></span> <span data-ttu-id="fb0bc-104">最後項目的欄位寬度小於或等於零，表示最後欄位是可變長度。</span><span class="sxs-lookup"><span data-stu-id="fb0bc-104">A field width less than or equal to zero in the last element indicates the last field is of variable length.</span></span>  
  
 <span data-ttu-id="fb0bc-105">作業失敗，因為除了最後項目以外的欄位寬度都設定為等於或小於零。</span><span class="sxs-lookup"><span data-stu-id="fb0bc-105">The operation has failed because a field width other than the last element is set to zero or less.</span></span> <span data-ttu-id="fb0bc-106">小於或等於零的欄位寬度可以用作最後項目，表示最後欄位是可變長度，但不能用作任何其他項目。</span><span class="sxs-lookup"><span data-stu-id="fb0bc-106">A field width less than or equal to zero can be used as the last element to indicate that the last field is of variable length, but it cannot be used as any other element.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fb0bc-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="fb0bc-107">To correct this error</span></span>  
  
-   <span data-ttu-id="fb0bc-108">將欄位寬度設定為正確的長度。</span><span class="sxs-lookup"><span data-stu-id="fb0bc-108">Set the field width to the correct length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb0bc-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="fb0bc-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths>  
 [<span data-ttu-id="fb0bc-110">如何：從固定寬度的文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="fb0bc-110">How to: Read From Fixed-width Text Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [<span data-ttu-id="fb0bc-111">TextFieldParser 物件</span><span class="sxs-lookup"><span data-stu-id="fb0bc-111">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
