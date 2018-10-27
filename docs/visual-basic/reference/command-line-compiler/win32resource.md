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
ms.openlocfilehash: 4ecac4ffe665d724d625aaeb7cc1e008eb13ca54
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50186079"
---
# <a name="-win32resource"></a><span data-ttu-id="cdbf7-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="cdbf7-102">-win32resource</span></span>
<span data-ttu-id="cdbf7-103">將 Win32 資源檔插入輸出檔。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdbf7-104">語法</span><span class="sxs-lookup"><span data-stu-id="cdbf7-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="cdbf7-105">引數</span><span class="sxs-lookup"><span data-stu-id="cdbf7-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="cdbf7-106">要加入至輸出檔的資源檔名稱。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="cdbf7-107">將檔案名稱括在引號 ("") 如果它包含空格。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdbf7-108">備註</span><span class="sxs-lookup"><span data-stu-id="cdbf7-108">Remarks</span></span>  
 <span data-ttu-id="cdbf7-109">您可以建立 Win32 資源檔與 Microsoft Windows 資源編譯器 (RC)。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="cdbf7-110">Win32 資源可以包含版本或點陣圖 （圖示） 資訊，以協助識別您的應用程式**檔案總管**。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="cdbf7-111">如果您未指定`-win32resource`，編譯器會產生的組件版本為基礎的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="cdbf7-112">`-win32resource`和`-win32icon`選項互斥。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="cdbf7-113">請參閱[-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)參考[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]資源檔，或[-資源 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)附加[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]資源檔。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdbf7-114">`-win32resource`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。</span><span class="sxs-lookup"><span data-stu-id="cdbf7-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdbf7-115">範例</span><span class="sxs-lookup"><span data-stu-id="cdbf7-115">Example</span></span>  
 <span data-ttu-id="cdbf7-116">下列程式碼會編譯`In.vb`並附加 Win32 資源檔， `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="cdbf7-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdbf7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdbf7-117">See Also</span></span>  
 [<span data-ttu-id="cdbf7-118">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="cdbf7-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="cdbf7-119">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="cdbf7-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
