---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: b7bfcb0f2034145822922126fe61efea8d8ef269
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344204"
---
# <a name="-libpath"></a><span data-ttu-id="447b1-102">-libpath</span><span class="sxs-lookup"><span data-stu-id="447b1-102">-libpath</span></span>
<span data-ttu-id="447b1-103">指定參考的組件的位置。</span><span class="sxs-lookup"><span data-stu-id="447b1-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="447b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="447b1-104">Syntax</span></span>  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="447b1-105">引數</span><span class="sxs-lookup"><span data-stu-id="447b1-105">Arguments</span></span>  
  
|<span data-ttu-id="447b1-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="447b1-106">Term</span></span>|<span data-ttu-id="447b1-107">定義</span><span class="sxs-lookup"><span data-stu-id="447b1-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="447b1-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="447b1-108">Required.</span></span> <span data-ttu-id="447b1-109">以分號分隔清單中的 改為查詢中參考的組件的目錄找不到在目前的工作目錄 （從中您叫用編譯器的目錄） 或 common language runtime 的系統目錄。</span><span class="sxs-lookup"><span data-stu-id="447b1-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="447b1-110">如果目錄名稱包含空格，將名稱括在引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="447b1-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="447b1-111">備註</span><span class="sxs-lookup"><span data-stu-id="447b1-111">Remarks</span></span>  
 <span data-ttu-id="447b1-112">`-libpath`選項會指定所參考的組件的位置[-參考](../../../visual-basic/reference/command-line-compiler/reference.md)選項。</span><span class="sxs-lookup"><span data-stu-id="447b1-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="447b1-113">編譯器會以下列順序搜尋不完整的組件參考：</span><span class="sxs-lookup"><span data-stu-id="447b1-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="447b1-114">目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="447b1-114">Current working directory.</span></span> <span data-ttu-id="447b1-115">這是叫用編譯器的起點目錄。</span><span class="sxs-lookup"><span data-stu-id="447b1-115">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="447b1-116">通用語言執行平台系統目錄。</span><span class="sxs-lookup"><span data-stu-id="447b1-116">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="447b1-117">所指定的目錄`/libpath`。</span><span class="sxs-lookup"><span data-stu-id="447b1-117">Directories specified by `/libpath`.</span></span>  
  
4. <span data-ttu-id="447b1-118">LIB 環境變數所指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="447b1-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="447b1-119">`-libpath`選項為加法; 指定超過一次附加到任何先前的值。</span><span class="sxs-lookup"><span data-stu-id="447b1-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="447b1-120">使用`-reference`來指定組件參考。</span><span class="sxs-lookup"><span data-stu-id="447b1-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="447b1-121">若要在 Visual Studio 中設定 /libpath 整合式開發環境</span><span class="sxs-lookup"><span data-stu-id="447b1-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="447b1-122">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="447b1-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="447b1-123">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="447b1-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="447b1-124">2.按一下 [參考] 節點。</span><span class="sxs-lookup"><span data-stu-id="447b1-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="447b1-125">3.按一下 [**參考路徑...** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="447b1-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="447b1-126">4.在 [**參考路徑**對話方塊方塊中，輸入中的目錄名稱**資料夾：** ] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="447b1-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="447b1-127">5.按一下 **將資料夾新增**。</span><span class="sxs-lookup"><span data-stu-id="447b1-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="447b1-128">範例</span><span class="sxs-lookup"><span data-stu-id="447b1-128">Example</span></span>  
 <span data-ttu-id="447b1-129">下列程式碼編譯`T2.vb`來建立.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="447b1-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="447b1-130">編譯器會將工作目錄中的 c： 磁碟機的根目錄中，c： 磁碟機的新組件目錄中尋找的組件參考。</span><span class="sxs-lookup"><span data-stu-id="447b1-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="447b1-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="447b1-131">See also</span></span>

- [<span data-ttu-id="447b1-132">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="447b1-132">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="447b1-133">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="447b1-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="447b1-134">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="447b1-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
