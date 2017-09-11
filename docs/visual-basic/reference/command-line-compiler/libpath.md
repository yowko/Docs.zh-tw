---
title: "/libpath |Microsoft 文件"
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
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: 16
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
ms.openlocfilehash: 7f24dd7707645f45677dcf7009e1adc64afaaa7c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="libpath"></a><span data-ttu-id="51571-102">/libpath</span><span class="sxs-lookup"><span data-stu-id="51571-102">/libpath</span></span>
<span data-ttu-id="51571-103">指定參考的組件的位置。</span><span class="sxs-lookup"><span data-stu-id="51571-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51571-104">語法</span><span class="sxs-lookup"><span data-stu-id="51571-104">Syntax</span></span>  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="51571-105">引數</span><span class="sxs-lookup"><span data-stu-id="51571-105">Arguments</span></span>  
  
|<span data-ttu-id="51571-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="51571-106">Term</span></span>|<span data-ttu-id="51571-107">定義</span><span class="sxs-lookup"><span data-stu-id="51571-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="51571-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="51571-108">Required.</span></span> <span data-ttu-id="51571-109">分號分隔清單的目錄中尋找參考的組件編譯器找不到在目前工作目錄 （從您所叫用編譯器的目錄） 或 common language runtime 的系統目錄。</span><span class="sxs-lookup"><span data-stu-id="51571-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="51571-110">如果目錄名稱包含空格，將名稱括在引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="51571-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51571-111">備註</span><span class="sxs-lookup"><span data-stu-id="51571-111">Remarks</span></span>  
 <span data-ttu-id="51571-112">`/libpath`選項會指定所參考的組件的位置[/參考](../../../visual-basic/reference/command-line-compiler/reference.md)選項。</span><span class="sxs-lookup"><span data-stu-id="51571-112">The `/libpath` option specifies the location of assemblies referenced by the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="51571-113">編譯器會搜尋以下列順序並未完整限定的組件參考︰</span><span class="sxs-lookup"><span data-stu-id="51571-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="51571-114">目前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="51571-114">Current working directory.</span></span> <span data-ttu-id="51571-115">這是從編譯器叫用的目錄。</span><span class="sxs-lookup"><span data-stu-id="51571-115">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="51571-116">通用語言執行階段系統目錄。</span><span class="sxs-lookup"><span data-stu-id="51571-116">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="51571-117">所指定的目錄`/libpath`。</span><span class="sxs-lookup"><span data-stu-id="51571-117">Directories specified by `/libpath`.</span></span>  
  
4.  <span data-ttu-id="51571-118">LIB 環境變數所指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="51571-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="51571-119">`/libpath`選項是加總; 指定它超過一次附加到任何先前的值。</span><span class="sxs-lookup"><span data-stu-id="51571-119">The `/libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="51571-120">使用`/reference`來指定組件參考。</span><span class="sxs-lookup"><span data-stu-id="51571-120">Use `/reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="51571-121">在 Visual Studio 中設定 /libpath 整合式開發環境</span><span class="sxs-lookup"><span data-stu-id="51571-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="51571-122">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="51571-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="51571-123">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="51571-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="51571-124">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="51571-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="51571-125">2.按一下 [**參考**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="51571-125">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="51571-126">3.按一下 [**參考路徑...** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="51571-126">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="51571-127">4.在**參考路徑** 對話方塊中，輸入中的目錄名稱**資料夾︰**方塊。</span><span class="sxs-lookup"><span data-stu-id="51571-127">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="51571-128">5.按一下 **新增資料夾**。</span><span class="sxs-lookup"><span data-stu-id="51571-128">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="51571-129">範例</span><span class="sxs-lookup"><span data-stu-id="51571-129">Example</span></span>  
 <span data-ttu-id="51571-130">下列程式碼編譯`T2.vb`建立的.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="51571-130">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="51571-131">編譯器會將工作目錄中，c︰ 磁碟機的根目錄和 c︰ 磁碟機的新組件目錄中尋找組件參考。</span><span class="sxs-lookup"><span data-stu-id="51571-131">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="51571-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51571-132">See Also</span></span>  
 <span data-ttu-id="51571-133">[組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="51571-133">[Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="51571-134"> [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="51571-134"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="51571-135"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="51571-135"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
