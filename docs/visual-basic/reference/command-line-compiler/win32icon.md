---
title: -win32icon
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95b2e2b4542f2e396a136f6a3d9baeb3e0c037a3
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-win32icon"></a><span data-ttu-id="17bd7-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="17bd7-102">-win32icon</span></span>
<span data-ttu-id="17bd7-103">將.ico 檔插入輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="17bd7-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="17bd7-104">這個.ico 檔表示中的輸出檔**檔案總管**。</span><span class="sxs-lookup"><span data-stu-id="17bd7-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17bd7-105">語法</span><span class="sxs-lookup"><span data-stu-id="17bd7-105">Syntax</span></span>  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="17bd7-106">引數</span><span class="sxs-lookup"><span data-stu-id="17bd7-106">Arguments</span></span>  
  
|<span data-ttu-id="17bd7-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="17bd7-107">Term</span></span>|<span data-ttu-id="17bd7-108">定義</span><span class="sxs-lookup"><span data-stu-id="17bd7-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="17bd7-109">要加入至輸出檔的.ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="17bd7-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="17bd7-110">將檔案名稱括在引號 ("") 如果包含空格。</span><span class="sxs-lookup"><span data-stu-id="17bd7-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17bd7-111">備註</span><span class="sxs-lookup"><span data-stu-id="17bd7-111">Remarks</span></span>  
 <span data-ttu-id="17bd7-112">您可以建立與 Microsoft Windows 資源編譯器 (RC) 的.ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="17bd7-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="17bd7-113">資源編譯器在編譯 Visual c + + 程式; 當叫用.ico 檔案是從.rc 檔案建立。</span><span class="sxs-lookup"><span data-stu-id="17bd7-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="17bd7-114">`-win32icon`和`-win32resource`選項互斥。</span><span class="sxs-lookup"><span data-stu-id="17bd7-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="17bd7-115">請參閱[-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)參考[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]資源檔或[-資源 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)附加[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]資源檔。</span><span class="sxs-lookup"><span data-stu-id="17bd7-115">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="17bd7-116">請參閱[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .res 檔案匯入。</span><span class="sxs-lookup"><span data-stu-id="17bd7-116">See [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="17bd7-117">若要設定-win32icon Visual Studio IDE 中</span><span class="sxs-lookup"><span data-stu-id="17bd7-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="17bd7-118">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="17bd7-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="17bd7-119">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="17bd7-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="17bd7-120">2.按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="17bd7-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="17bd7-121">3.修改中的值**圖示**方塊。</span><span class="sxs-lookup"><span data-stu-id="17bd7-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="17bd7-122">範例</span><span class="sxs-lookup"><span data-stu-id="17bd7-122">Example</span></span>  
 <span data-ttu-id="17bd7-123">下列程式碼編譯`In.vb`，並將.ico 檔，附加`Rf.ico`。</span><span class="sxs-lookup"><span data-stu-id="17bd7-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="17bd7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17bd7-124">See Also</span></span>  
 [<span data-ttu-id="17bd7-125">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="17bd7-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="17bd7-126">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="17bd7-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
