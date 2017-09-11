---
title: "模組 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- modules, Visual Basic
ms.assetid: 370bfc90-e8f2-4942-bdec-9897ce605d31
caps.latest.revision: 11
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
ms.openlocfilehash: 808510c83339e1768dba39f119a2e97ac44f0e4a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="modules-visual-basic"></a><span data-ttu-id="3d22d-102">模組 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d22d-102">Modules (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="3d22d-103">提供數個模組，讓您簡化一般工作，包括管理字串，執行數學計算，取得系統資訊、 執行檔案和目錄的作業，在您的程式碼中等等。</span><span class="sxs-lookup"><span data-stu-id="3d22d-103"> provides several modules that enable you to simplify common tasks in your code, including manipulating strings, performing mathematical calculations, getting system information, performing file and directory operations, and so on.</span></span> <span data-ttu-id="3d22d-104">下表列出所提供的模組[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3d22d-104">The following table lists the modules provided by [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="3d22d-105"><xref:Microsoft.VisualBasic.Constants></xref:Microsoft.VisualBasic.Constants></span><span class="sxs-lookup"><span data-stu-id="3d22d-105"><xref:Microsoft.VisualBasic.Constants></span></span>|<span data-ttu-id="3d22d-106">包含其他的常數。</span><span class="sxs-lookup"><span data-stu-id="3d22d-106">Contains miscellaneous constants.</span></span> <span data-ttu-id="3d22d-107">這些常數可以在程式碼中任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="3d22d-107">These constants can be used anywhere in your code.</span></span>|  
|<span data-ttu-id="3d22d-108"><xref:Microsoft.VisualBasic.ControlChars></xref:Microsoft.VisualBasic.ControlChars></span><span class="sxs-lookup"><span data-stu-id="3d22d-108"><xref:Microsoft.VisualBasic.ControlChars></span></span>|<span data-ttu-id="3d22d-109">包含常數控制字元來列印及顯示文字。</span><span class="sxs-lookup"><span data-stu-id="3d22d-109">Contains constant control characters for printing and displaying text.</span></span>|  
|<span data-ttu-id="3d22d-110"><xref:Microsoft.VisualBasic.Conversion></xref:Microsoft.VisualBasic.Conversion></span><span class="sxs-lookup"><span data-stu-id="3d22d-110"><xref:Microsoft.VisualBasic.Conversion></span></span>|<span data-ttu-id="3d22d-111">包含數字字串、 數字的字串和一個資料輸入到另一個十進位數字轉換成其他的基底的成員。</span><span class="sxs-lookup"><span data-stu-id="3d22d-111">Contains members that convert decimal numbers to other bases, numbers to strings, strings to numbers, and one data type to another.</span></span>|  
|<span data-ttu-id="3d22d-112"><xref:Microsoft.VisualBasic.DateAndTime></xref:Microsoft.VisualBasic.DateAndTime></span><span class="sxs-lookup"><span data-stu-id="3d22d-112"><xref:Microsoft.VisualBasic.DateAndTime></span></span>|<span data-ttu-id="3d22d-113">包含成員，取得目前的日期或時間、 執行日期計算傳回日期或時間，設定日期或時間，或處理程序的持續時間的時間。</span><span class="sxs-lookup"><span data-stu-id="3d22d-113">Contains members that get the current date or time, perform date calculations, return a date or time, set the date or time, or time the duration of a process.</span></span>|  
|<span data-ttu-id="3d22d-114"><xref:Microsoft.VisualBasic.ErrObject></xref:Microsoft.VisualBasic.ErrObject></span><span class="sxs-lookup"><span data-stu-id="3d22d-114"><xref:Microsoft.VisualBasic.ErrObject></span></span>|<span data-ttu-id="3d22d-115">包含執行階段錯誤和方法引發，或清除錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3d22d-115">Contains information about run-time errors and methods to raise or clear an error.</span></span>|  
|<span data-ttu-id="3d22d-116"><xref:Microsoft.VisualBasic.FileSystem></xref:Microsoft.VisualBasic.FileSystem></span><span class="sxs-lookup"><span data-stu-id="3d22d-116"><xref:Microsoft.VisualBasic.FileSystem></span></span>|<span data-ttu-id="3d22d-117">包含執行檔案、 目錄或資料夾，以及系統作業的成員。</span><span class="sxs-lookup"><span data-stu-id="3d22d-117">Contains members that perform file, directory or folder, and system operations.</span></span>|  
|<span data-ttu-id="3d22d-118"><xref:Microsoft.VisualBasic.Financial></xref:Microsoft.VisualBasic.Financial></span><span class="sxs-lookup"><span data-stu-id="3d22d-118"><xref:Microsoft.VisualBasic.Financial></span></span>|<span data-ttu-id="3d22d-119">包含用來執行財務計算程序。</span><span class="sxs-lookup"><span data-stu-id="3d22d-119">Contains procedures that are used to perform financial calculations.</span></span>|  
|<span data-ttu-id="3d22d-120"><xref:Microsoft.VisualBasic.Globals></xref:Microsoft.VisualBasic.Globals></span><span class="sxs-lookup"><span data-stu-id="3d22d-120"><xref:Microsoft.VisualBasic.Globals></span></span>|<span data-ttu-id="3d22d-121">包含目前的指令碼引擎版本的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3d22d-121">Contains information about the current scripting engine version.</span></span>|  
|<span data-ttu-id="3d22d-122"><xref:Microsoft.VisualBasic.Information></xref:Microsoft.VisualBasic.Information></span><span class="sxs-lookup"><span data-stu-id="3d22d-122"><xref:Microsoft.VisualBasic.Information></span></span>|<span data-ttu-id="3d22d-123">包含的成員，傳回、 測試，或確認資訊，例如陣列的大小、 類型名稱等等。</span><span class="sxs-lookup"><span data-stu-id="3d22d-123">Contains the members that return, test for, or verify information such as array size, type names, and so on.</span></span>|  
|<span data-ttu-id="3d22d-124"><xref:Microsoft.VisualBasic.Interaction></xref:Microsoft.VisualBasic.Interaction></span><span class="sxs-lookup"><span data-stu-id="3d22d-124"><xref:Microsoft.VisualBasic.Interaction></span></span>|<span data-ttu-id="3d22d-125">包含與物件、 應用程式和系統互動的成員。</span><span class="sxs-lookup"><span data-stu-id="3d22d-125">Contains members interact with objects, applications, and systems.</span></span>|  
|<span data-ttu-id="3d22d-126"><xref:Microsoft.VisualBasic.Strings></xref:Microsoft.VisualBasic.Strings></span><span class="sxs-lookup"><span data-stu-id="3d22d-126"><xref:Microsoft.VisualBasic.Strings></span></span>|<span data-ttu-id="3d22d-127">包含執行字串作業，例如重新格式化字串，搜尋字串，取得字串，長度等等的成員。</span><span class="sxs-lookup"><span data-stu-id="3d22d-127">Contains members that perform string operations such as reformatting strings, searching a string, getting the length of a string, and so on.</span></span>|  
|<span data-ttu-id="3d22d-128"><xref:Microsoft.VisualBasic.VBMath></xref:Microsoft.VisualBasic.VBMath></span><span class="sxs-lookup"><span data-stu-id="3d22d-128"><xref:Microsoft.VisualBasic.VBMath></span></span>|<span data-ttu-id="3d22d-129">包含成員執行數學運算。</span><span class="sxs-lookup"><span data-stu-id="3d22d-129">Contains members perform mathematical operations.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d22d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d22d-130">See Also</span></span>  
 <span data-ttu-id="3d22d-131">[Visual Basic 語言參考](../../visual-basic/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="3d22d-131">[Visual Basic Language Reference](../../visual-basic/language-reference/index.md) </span></span>  
<span data-ttu-id="3d22d-132"> [Visual Basic](../../visual-basic/index.md)</span><span class="sxs-lookup"><span data-stu-id="3d22d-132"> [Visual Basic](../../visual-basic/index.md)</span></span>
