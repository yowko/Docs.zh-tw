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
ms.openlocfilehash: 442e271c7661ece24baff966cee5fe866d783eab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="all-field-widths-except-the-last-element-must-be-greater-than-zero"></a><span data-ttu-id="09c4f-102">除了最後項目以外的所有欄位寬度都必須大於零</span><span class="sxs-lookup"><span data-stu-id="09c4f-102">All field widths, except the last element, must be greater than zero</span></span>
<span data-ttu-id="09c4f-103">除了最後項目以外的所有欄位寬度都必須大於零。</span><span class="sxs-lookup"><span data-stu-id="09c4f-103">All field widths, except the last element, must be greater than zero.</span></span> <span data-ttu-id="09c4f-104">最後項目的欄位寬度小於或等於零，表示最後欄位是可變長度。</span><span class="sxs-lookup"><span data-stu-id="09c4f-104">A field width less than or equal to zero in the last element indicates the last field is of variable length.</span></span>  
  
 <span data-ttu-id="09c4f-105">作業失敗，因為除了最後項目以外的欄位寬度都設定為等於或小於零。</span><span class="sxs-lookup"><span data-stu-id="09c4f-105">The operation has failed because a field width other than the last element is set to zero or less.</span></span> <span data-ttu-id="09c4f-106">小於或等於零的欄位寬度可以用作最後項目，表示最後欄位是可變長度，但不能用作任何其他項目。</span><span class="sxs-lookup"><span data-stu-id="09c4f-106">A field width less than or equal to zero can be used as the last element to indicate that the last field is of variable length, but it cannot be used as any other element.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="09c4f-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="09c4f-107">To correct this error</span></span>  
  
-   <span data-ttu-id="09c4f-108">將欄位寬度設定為正確的長度。</span><span class="sxs-lookup"><span data-stu-id="09c4f-108">Set the field width to the correct length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09c4f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09c4f-109">See Also</span></span>  
 [<span data-ttu-id="09c4f-110">TextFieldParser.SetFieldWidths 方法</span><span class="sxs-lookup"><span data-stu-id="09c4f-110">TextFieldParser.SetFieldWidths Method</span></span>](http://msdn.microsoft.com/en-us/958fed9f-e0f3-4fc5-83b4-386156bdf036)  
 [<span data-ttu-id="09c4f-111">TextFieldParser.FieldWidths 屬性</span><span class="sxs-lookup"><span data-stu-id="09c4f-111">TextFieldParser.FieldWidths Property</span></span>](http://msdn.microsoft.com/en-us/c6985360-60c6-494e-89e7-43b6b73f2597)  
 [<span data-ttu-id="09c4f-112">如何：從固定寬度的文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="09c4f-112">How to: Read From Fixed-width Text Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [<span data-ttu-id="09c4f-113">TextFieldParser 物件</span><span class="sxs-lookup"><span data-stu-id="09c4f-113">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
