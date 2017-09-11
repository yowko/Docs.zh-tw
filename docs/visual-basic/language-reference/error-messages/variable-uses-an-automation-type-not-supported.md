---
title: "變數會使用不支援在 Visual Basic 中的 Automation 類型 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID458
dev_langs:
- VB
ms.assetid: bde4f4da-493b-452c-b6e4-1d370edba4cd
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 74c4472230a3a8c54859771c0b2f7fc954ac0966
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="variable-uses-an-automation-type-not-supported-in-visual-basic"></a><span data-ttu-id="bac3c-102">變數使用在 Visual Basic 中不支援的 Automation 類型</span><span class="sxs-lookup"><span data-stu-id="bac3c-102">Variable uses an Automation type not supported in Visual Basic</span></span>
<span data-ttu-id="bac3c-103">您嘗試使用型別程式庫或不支援的資料類型的物件程式庫中定義的變數[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bac3c-103">You tried to use a variable defined in a type library or object library that has a data type not supported by [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bac3c-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="bac3c-104">To correct this error</span></span>  
  
-   <span data-ttu-id="bac3c-105">使用可辨識之型別的變數[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bac3c-105">Use a variable of a type recognized by [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
     <span data-ttu-id="bac3c-106">-或-</span><span class="sxs-lookup"><span data-stu-id="bac3c-106">-or-</span></span>  
  
-   <span data-ttu-id="bac3c-107">如果您遇到這個錯誤時使用`FileGet`或`FileGetOBject`，請確定您嘗試使用的檔案寫入與`FilePut`或`FilePutObject`。</span><span class="sxs-lookup"><span data-stu-id="bac3c-107">If you encounter this error while using `FileGet` or `FileGetOBject`, make sure the file you are trying to use was written to with `FilePut` or `FilePutObject`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac3c-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bac3c-108">See Also</span></span>  
 [<span data-ttu-id="bac3c-109">資料類型</span><span class="sxs-lookup"><span data-stu-id="bac3c-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)
