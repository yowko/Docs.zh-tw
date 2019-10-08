---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: 8f4e415576562885c9edbd3d2dddbe2a271e9923
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005462"
---
# <a name="-libpath"></a><span data-ttu-id="cb0cb-102">-libpath</span><span class="sxs-lookup"><span data-stu-id="cb0cb-102">-libpath</span></span>
<span data-ttu-id="cb0cb-103">指定參考元件的位置。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb0cb-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb0cb-104">Syntax</span></span>  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="cb0cb-105">引數</span><span class="sxs-lookup"><span data-stu-id="cb0cb-105">Arguments</span></span>  
  
|<span data-ttu-id="cb0cb-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="cb0cb-106">Term</span></span>|<span data-ttu-id="cb0cb-107">定義</span><span class="sxs-lookup"><span data-stu-id="cb0cb-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="cb0cb-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-108">Required.</span></span> <span data-ttu-id="cb0cb-109">以分號分隔的目錄清單，如果在目前的工作目錄（您叫用編譯器的目錄）或 common language runtime 的系統目錄中找不到參考的元件，則為要查看的目錄。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="cb0cb-110">如果目錄名稱包含空格，請將名稱括在引號（""）中。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb0cb-111">備註</span><span class="sxs-lookup"><span data-stu-id="cb0cb-111">Remarks</span></span>  
 <span data-ttu-id="cb0cb-112">@No__t-0 選項會指定[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)選項所參考之元件的位置。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="cb0cb-113">編譯器會以下列順序搜尋不完整的組件參考：</span><span class="sxs-lookup"><span data-stu-id="cb0cb-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="cb0cb-114">目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-114">Current working directory.</span></span> <span data-ttu-id="cb0cb-115">這是叫用編譯器的起點目錄。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-115">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="cb0cb-116">通用語言執行平台系統目錄。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-116">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="cb0cb-117">@No__t-0 指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-117">Directories specified by `/libpath`.</span></span>  
  
4. <span data-ttu-id="cb0cb-118">LIB 環境變數所指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="cb0cb-119">@No__t-0 選項為加法;指定超過一次以上會附加到任何先前的值。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="cb0cb-120">使用 `-reference` 來指定元件參考。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="cb0cb-121">在 Visual Studio 的整合式開發環境中設定/libpath</span><span class="sxs-lookup"><span data-stu-id="cb0cb-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="cb0cb-122">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="cb0cb-123">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="cb0cb-124">2.按一下 [參考] 節點。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="cb0cb-125">3.按一下 [**參考路徑 ...** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="cb0cb-126">4.在 [**參考路徑**] 對話方塊的 [**資料夾：** ] 方塊中，輸入目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="cb0cb-127">5.按一下 [**新增資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cb0cb-128">範例</span><span class="sxs-lookup"><span data-stu-id="cb0cb-128">Example</span></span>  
 <span data-ttu-id="cb0cb-129">下列程式碼會編譯 `T2.vb`，以建立 .exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="cb0cb-130">編譯器會查看工作目錄、C：磁片磁碟機的根目錄，以及 C：磁片磁碟機的新元件目錄中的元件參考。</span><span class="sxs-lookup"><span data-stu-id="cb0cb-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb0cb-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb0cb-131">See also</span></span>

- [<span data-ttu-id="cb0cb-132">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="cb0cb-132">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="cb0cb-133">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="cb0cb-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="cb0cb-134">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="cb0cb-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
