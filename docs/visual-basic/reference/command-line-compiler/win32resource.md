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
ms.openlocfilehash: 382dcc6571aa06ecdfc32bf43080c4b7a36eb1f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961294"
---
# <a name="-win32resource"></a><span data-ttu-id="53681-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="53681-102">-win32resource</span></span>
<span data-ttu-id="53681-103">將 Win32 資源檔插入輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="53681-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53681-104">語法</span><span class="sxs-lookup"><span data-stu-id="53681-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="53681-105">引數</span><span class="sxs-lookup"><span data-stu-id="53681-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="53681-106">要新增至輸出檔的資源檔名稱。</span><span class="sxs-lookup"><span data-stu-id="53681-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="53681-107">將檔案名括在引號 ("") 中 (如果它包含空格)。</span><span class="sxs-lookup"><span data-stu-id="53681-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53681-108">備註</span><span class="sxs-lookup"><span data-stu-id="53681-108">Remarks</span></span>  
 <span data-ttu-id="53681-109">您可以使用 Microsoft Windows 資源編譯器 (RC) 來建立 Win32 資源檔。</span><span class="sxs-lookup"><span data-stu-id="53681-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="53681-110">Win32 資源可以包含版本或點陣圖 (圖示) 資訊, 協助您在 [檔案**瀏覽器**] 中識別您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="53681-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="53681-111">如果您未指定`-win32resource`, 編譯器會根據元件版本產生版本資訊。</span><span class="sxs-lookup"><span data-stu-id="53681-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="53681-112">`-win32resource` 和`-win32icon`選項互斥。</span><span class="sxs-lookup"><span data-stu-id="53681-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="53681-113">請參閱[-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)來參考 .NET Framework 資源檔, 或使用[-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)來附加 .NET Framework 資源檔。</span><span class="sxs-lookup"><span data-stu-id="53681-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a .NET Framework resource file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53681-114">此`-win32resource`選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時, 才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="53681-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53681-115">範例</span><span class="sxs-lookup"><span data-stu-id="53681-115">Example</span></span>  
 <span data-ttu-id="53681-116">下列程式碼會`In.vb`編譯並附加 Win32 資源`Rf.res`檔:</span><span class="sxs-lookup"><span data-stu-id="53681-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="53681-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53681-117">See also</span></span>

- [<span data-ttu-id="53681-118">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="53681-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="53681-119">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="53681-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
