---
title: -libpath
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cff59d9b406045b4522d3a7d6e85528513214635
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-libpath"></a><span data-ttu-id="315c6-102">-libpath</span><span class="sxs-lookup"><span data-stu-id="315c6-102">-libpath</span></span>
<span data-ttu-id="315c6-103">指定的參考組件的位置。</span><span class="sxs-lookup"><span data-stu-id="315c6-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="315c6-104">語法</span><span class="sxs-lookup"><span data-stu-id="315c6-104">Syntax</span></span>  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="315c6-105">引數</span><span class="sxs-lookup"><span data-stu-id="315c6-105">Arguments</span></span>  
  
|<span data-ttu-id="315c6-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="315c6-106">Term</span></span>|<span data-ttu-id="315c6-107">定義</span><span class="sxs-lookup"><span data-stu-id="315c6-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="315c6-108">必要。</span><span class="sxs-lookup"><span data-stu-id="315c6-108">Required.</span></span> <span data-ttu-id="315c6-109">以分號分隔清單的編譯器，如果查詢參考的組件的目錄找不到在目前工作目錄 (directory 叫編譯器) 或 common language runtime 的系統目錄。</span><span class="sxs-lookup"><span data-stu-id="315c6-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="315c6-110">如果目錄名稱包含空格，將名稱括在引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="315c6-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="315c6-111">備註</span><span class="sxs-lookup"><span data-stu-id="315c6-111">Remarks</span></span>  
 <span data-ttu-id="315c6-112">`-libpath`選項會指定所參考的組件位置[-參考](../../../visual-basic/reference/command-line-compiler/reference.md)選項。</span><span class="sxs-lookup"><span data-stu-id="315c6-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="315c6-113">編譯器會以下列順序搜尋不完整的組件參考：</span><span class="sxs-lookup"><span data-stu-id="315c6-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="315c6-114">目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="315c6-114">Current working directory.</span></span> <span data-ttu-id="315c6-115">這是叫用編譯器的起點目錄。</span><span class="sxs-lookup"><span data-stu-id="315c6-115">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="315c6-116">通用語言執行平台系統目錄。</span><span class="sxs-lookup"><span data-stu-id="315c6-116">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="315c6-117">所指定的目錄`/libpath`。</span><span class="sxs-lookup"><span data-stu-id="315c6-117">Directories specified by `/libpath`.</span></span>  
  
4.  <span data-ttu-id="315c6-118">LIB 環境變數所指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="315c6-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="315c6-119">`-libpath`選項是加總，則指定它超過一次將附加至任何先前的值。</span><span class="sxs-lookup"><span data-stu-id="315c6-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="315c6-120">使用`-reference`來指定組件參考。</span><span class="sxs-lookup"><span data-stu-id="315c6-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="315c6-121">在 Visual Studio 中設定 /libpath 整合式開發環境</span><span class="sxs-lookup"><span data-stu-id="315c6-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="315c6-122">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="315c6-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="315c6-123">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="315c6-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="315c6-124">2.按一下 [參考] 節點。</span><span class="sxs-lookup"><span data-stu-id="315c6-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="315c6-125">3.按一下**參考路徑...**  按鈕。</span><span class="sxs-lookup"><span data-stu-id="315c6-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="315c6-126">4.在**參考路徑**對話方塊方塊中，輸入中的目錄名稱**資料夾：**方塊。</span><span class="sxs-lookup"><span data-stu-id="315c6-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="315c6-127">5.按一下**加入資料夾**。</span><span class="sxs-lookup"><span data-stu-id="315c6-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="315c6-128">範例</span><span class="sxs-lookup"><span data-stu-id="315c6-128">Example</span></span>  
 <span data-ttu-id="315c6-129">下列程式碼編譯`T2.vb`建立.exe 檔。</span><span class="sxs-lookup"><span data-stu-id="315c6-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="315c6-130">編譯器會尋找組件參考的工作目錄、 c： 磁碟機的根目錄和新的組件目錄中的 c： 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="315c6-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="315c6-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="315c6-131">See Also</span></span>  
 [<span data-ttu-id="315c6-132">組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="315c6-132">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="315c6-133">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="315c6-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="315c6-134">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="315c6-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
