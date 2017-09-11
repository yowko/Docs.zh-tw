---
title: "/win32icon |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: 13
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
ms.openlocfilehash: f7d451026438be722d6cb7eecfffe397ccff82ae
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="win32icon"></a><span data-ttu-id="590c5-102">/win32icon</span><span class="sxs-lookup"><span data-stu-id="590c5-102">/win32icon</span></span>
<span data-ttu-id="590c5-103">將.ico 檔案插入至輸出檔。</span><span class="sxs-lookup"><span data-stu-id="590c5-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="590c5-104">這個.ico 檔案表示中的輸出檔**檔案總管**。</span><span class="sxs-lookup"><span data-stu-id="590c5-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="590c5-105">語法</span><span class="sxs-lookup"><span data-stu-id="590c5-105">Syntax</span></span>  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="590c5-106">引數</span><span class="sxs-lookup"><span data-stu-id="590c5-106">Arguments</span></span>  
  
|<span data-ttu-id="590c5-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="590c5-107">Term</span></span>|<span data-ttu-id="590c5-108">定義</span><span class="sxs-lookup"><span data-stu-id="590c5-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="590c5-109">要加入至輸出檔的.ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="590c5-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="590c5-110">將檔案名稱括在引號 ("") 如果它包含空格。</span><span class="sxs-lookup"><span data-stu-id="590c5-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="590c5-111">備註</span><span class="sxs-lookup"><span data-stu-id="590c5-111">Remarks</span></span>  
 <span data-ttu-id="590c5-112">您可以建立.ico 檔與 Microsoft Windows 資源編譯器 (RC)。</span><span class="sxs-lookup"><span data-stu-id="590c5-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="590c5-113">資源編譯器會叫用，當您編譯 Visual c + + 程式。.ico 檔案是從.rc 檔案建立。</span><span class="sxs-lookup"><span data-stu-id="590c5-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="590c5-114">`/win32icon`和`/win32resource`選項互斥。</span><span class="sxs-lookup"><span data-stu-id="590c5-114">The `/win32icon` and `/win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="590c5-115">請參閱[/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)參考[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]資源檔或[/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)附加[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]資源檔。</span><span class="sxs-lookup"><span data-stu-id="590c5-115">See [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file, or [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file.</span></span> <span data-ttu-id="590c5-116">請參閱[/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .res 檔案匯入。</span><span class="sxs-lookup"><span data-stu-id="590c5-116">See [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="590c5-117">在 Visual Studio IDE 中設定 /win32icon</span><span class="sxs-lookup"><span data-stu-id="590c5-117">To set /win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="590c5-118">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="590c5-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="590c5-119">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="590c5-119">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="590c5-120">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="590c5-120">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="590c5-121">2.按一下 [應用程式] **** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="590c5-121">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="590c5-122">3.修改中的值**圖示**方塊。</span><span class="sxs-lookup"><span data-stu-id="590c5-122">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="590c5-123">範例</span><span class="sxs-lookup"><span data-stu-id="590c5-123">Example</span></span>  
 <span data-ttu-id="590c5-124">下列程式碼編譯`In.vb`並附加.ico 檔， `Rf.ico`。</span><span class="sxs-lookup"><span data-stu-id="590c5-124">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="590c5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="590c5-125">See Also</span></span>  
 <span data-ttu-id="590c5-126">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="590c5-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="590c5-127"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="590c5-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
