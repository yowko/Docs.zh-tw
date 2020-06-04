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
ms.openlocfilehash: bcbc690690993a094bc5360d0c13bddebf8cd615
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414242"
---
# <a name="-win32resource"></a><span data-ttu-id="837dc-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="837dc-102">-win32resource</span></span>
<span data-ttu-id="837dc-103">將 Win32 資源檔插入輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="837dc-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="837dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="837dc-104">Syntax</span></span>  
  
```console  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="837dc-105">引數</span><span class="sxs-lookup"><span data-stu-id="837dc-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="837dc-106">要新增至輸出檔的資源檔名稱。</span><span class="sxs-lookup"><span data-stu-id="837dc-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="837dc-107">將檔案名括在引號（""）中（如果它包含空格）。</span><span class="sxs-lookup"><span data-stu-id="837dc-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="837dc-108">備註</span><span class="sxs-lookup"><span data-stu-id="837dc-108">Remarks</span></span>  
 <span data-ttu-id="837dc-109">您可以使用 Microsoft Windows 資源編譯器（RC）來建立 Win32 資源檔。</span><span class="sxs-lookup"><span data-stu-id="837dc-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="837dc-110">Win32 資源可以包含版本或點陣圖（圖示）資訊，協助您在 [檔案**瀏覽器**] 中識別您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="837dc-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="837dc-111">如果您未指定 `-win32resource` ，編譯器會根據元件版本產生版本資訊。</span><span class="sxs-lookup"><span data-stu-id="837dc-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="837dc-112">`-win32resource` 和 `-win32icon` 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="837dc-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="837dc-113">請參閱[-linkresource （Visual Basic）](linkresource.md)來參考 .NET Framework 資源檔，或使用[-resource （Visual Basic）](resource.md)來附加 .NET Framework 資源檔。</span><span class="sxs-lookup"><span data-stu-id="837dc-113">See [-linkresource (Visual Basic)](linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](resource.md) to attach a .NET Framework resource file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="837dc-114">此 `-win32resource` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="837dc-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="837dc-115">範例</span><span class="sxs-lookup"><span data-stu-id="837dc-115">Example</span></span>  
 <span data-ttu-id="837dc-116">下列程式碼會編譯 `In.vb` 並附加 Win32 資源檔 `Rf.res` ：</span><span class="sxs-lookup"><span data-stu-id="837dc-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="837dc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="837dc-117">See also</span></span>

- [<span data-ttu-id="837dc-118">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="837dc-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="837dc-119">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="837dc-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
