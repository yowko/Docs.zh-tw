---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: cee06adec89aac4b3e3f170df3bf932e466f3070
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004957"
---
# <a name="-win32resource"></a><span data-ttu-id="e757b-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="e757b-102">-win32resource</span></span>
<span data-ttu-id="e757b-103">將 Win32 資源檔插入輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="e757b-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e757b-104">語法</span><span class="sxs-lookup"><span data-stu-id="e757b-104">Syntax</span></span>  
  
```console  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="e757b-105">引數</span><span class="sxs-lookup"><span data-stu-id="e757b-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="e757b-106">要新增至輸出檔的資源檔名稱。</span><span class="sxs-lookup"><span data-stu-id="e757b-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="e757b-107">將檔案名括在引號（""）中（如果它包含空格）。</span><span class="sxs-lookup"><span data-stu-id="e757b-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e757b-108">備註</span><span class="sxs-lookup"><span data-stu-id="e757b-108">Remarks</span></span>  
 <span data-ttu-id="e757b-109">您可以使用 Microsoft Windows 資源編譯器（RC）來建立 Win32 資源檔。</span><span class="sxs-lookup"><span data-stu-id="e757b-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="e757b-110">Win32 資源可以包含版本或點陣圖（圖示）資訊，協助您在 [檔案**瀏覽器**] 中識別您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e757b-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="e757b-111">如果您未指定 `-win32resource`，則編譯器會根據元件版本產生版本資訊。</span><span class="sxs-lookup"><span data-stu-id="e757b-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="e757b-112">@No__t-0 和 @no__t 1 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="e757b-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="e757b-113">請參閱[-linkresource （Visual Basic）](../../../visual-basic/reference/command-line-compiler/linkresource.md)來參考 .NET Framework 資源檔，或使用[-resource （Visual Basic）](../../../visual-basic/reference/command-line-compiler/resource.md)來附加 .NET Framework 資源檔。</span><span class="sxs-lookup"><span data-stu-id="e757b-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a .NET Framework resource file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e757b-114">@No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="e757b-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e757b-115">範例</span><span class="sxs-lookup"><span data-stu-id="e757b-115">Example</span></span>  
 <span data-ttu-id="e757b-116">下列程式碼會編譯 `In.vb`，並將 Win32 資源檔附加 `Rf.res`：</span><span class="sxs-lookup"><span data-stu-id="e757b-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e757b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e757b-117">See also</span></span>

- [<span data-ttu-id="e757b-118">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="e757b-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e757b-119">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="e757b-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
