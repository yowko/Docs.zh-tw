---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 6b4b69d227c857442de6857fac023090b3698e81
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004640"
---
# <a name="-win32icon"></a><span data-ttu-id="e8de7-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="e8de7-102">-win32icon</span></span>
<span data-ttu-id="e8de7-103">在輸出檔中插入 .ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="e8de7-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="e8de7-104">這個 .ico 檔案代表檔案**瀏覽器**中的輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="e8de7-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8de7-105">語法</span><span class="sxs-lookup"><span data-stu-id="e8de7-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="e8de7-106">引數</span><span class="sxs-lookup"><span data-stu-id="e8de7-106">Arguments</span></span>  
  
|<span data-ttu-id="e8de7-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="e8de7-107">Term</span></span>|<span data-ttu-id="e8de7-108">定義</span><span class="sxs-lookup"><span data-stu-id="e8de7-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="e8de7-109">要加入至輸出檔的 .ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="e8de7-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="e8de7-110">將檔案名括在引號（""）中（如果它包含空格）。</span><span class="sxs-lookup"><span data-stu-id="e8de7-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8de7-111">備註</span><span class="sxs-lookup"><span data-stu-id="e8de7-111">Remarks</span></span>  
 <span data-ttu-id="e8de7-112">您可以使用 Microsoft Windows 資源編譯器（RC）來建立 .ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="e8de7-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="e8de7-113">當您編譯視覺效果C++程式時，會叫用資源編譯器;會從 .rc 檔案建立 .ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="e8de7-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="e8de7-114">@No__t-0 和 @no__t 1 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="e8de7-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="e8de7-115">請參閱[-linkresource （Visual Basic）](../../../visual-basic/reference/command-line-compiler/linkresource.md)來參考 .NET Framework 資源檔，或使用[-resource （Visual Basic）](../../../visual-basic/reference/command-line-compiler/resource.md)來附加 .NET Framework 資源檔。</span><span class="sxs-lookup"><span data-stu-id="e8de7-115">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a .NET Framework resource file.</span></span> <span data-ttu-id="e8de7-116">請參閱[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)以匯入 .res 檔案。</span><span class="sxs-lookup"><span data-stu-id="e8de7-116">See [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="e8de7-117">若要在 Visual Studio IDE 中設定-win32icon</span><span class="sxs-lookup"><span data-stu-id="e8de7-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="e8de7-118">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="e8de7-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e8de7-119">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="e8de7-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="e8de7-120">2.按一下 [應用程式] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e8de7-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="e8de7-121">3.修改 [**圖示**] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="e8de7-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e8de7-122">範例</span><span class="sxs-lookup"><span data-stu-id="e8de7-122">Example</span></span>  
 <span data-ttu-id="e8de7-123">下列程式碼會編譯 `In.vb`，並將 .ico 檔案附加 `Rf.ico`。</span><span class="sxs-lookup"><span data-stu-id="e8de7-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8de7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8de7-124">See also</span></span>

- [<span data-ttu-id="e8de7-125">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="e8de7-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e8de7-126">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="e8de7-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
