---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 162c7d58350c381ec667e8a4cd11c03e83fcdf44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654761"
---
# <a name="-sdkpath"></a><span data-ttu-id="f2196-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="f2196-102">-sdkpath</span></span>
<span data-ttu-id="f2196-103">指定 mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。</span><span class="sxs-lookup"><span data-stu-id="f2196-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2196-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2196-104">Syntax</span></span>  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="f2196-105">引數</span><span class="sxs-lookup"><span data-stu-id="f2196-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="f2196-106">包含 mscorlib.dll 和 Microsoft.VisualBasic.dll 用於編譯的版本的目錄。</span><span class="sxs-lookup"><span data-stu-id="f2196-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="f2196-107">未驗證此路徑，直到它載入。</span><span class="sxs-lookup"><span data-stu-id="f2196-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="f2196-108">將目錄名稱括在引號 ("") 如果包含空格。</span><span class="sxs-lookup"><span data-stu-id="f2196-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2196-109">備註</span><span class="sxs-lookup"><span data-stu-id="f2196-109">Remarks</span></span>  
 <span data-ttu-id="f2196-110">此選項會告知 Visual Basic 編譯器，從非預設位置載入 mscorlib.dll 和 Microsoft.VisualBasic.dll 的檔案。</span><span class="sxs-lookup"><span data-stu-id="f2196-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="f2196-111">`-sdkpath`選項設計用來搭配[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)。</span><span class="sxs-lookup"><span data-stu-id="f2196-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="f2196-112">[!INCLUDE[Compact](~/includes/compact-md.md)]會使用不同版本的支援程式庫，以避免使用的類型和語言功能的裝置上找不到。</span><span class="sxs-lookup"><span data-stu-id="f2196-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2196-113">`-sdkpath`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。</span><span class="sxs-lookup"><span data-stu-id="f2196-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="f2196-114">`-sdkpath` Visual Basic 裝置專案載入時，設定選項。</span><span class="sxs-lookup"><span data-stu-id="f2196-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="f2196-115">您可以指定編譯器應該使用編譯 Visual Basic 執行階段程式庫的參考不`-vbruntime`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="f2196-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="f2196-116">如需詳細資訊，請參閱[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)。</span><span class="sxs-lookup"><span data-stu-id="f2196-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2196-117">範例</span><span class="sxs-lookup"><span data-stu-id="f2196-117">Example</span></span>  
 <span data-ttu-id="f2196-118">下列程式碼編譯`Myfile.vb`與[!INCLUDE[Compact](~/includes/compact-md.md)]，使用 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的版本中的預設安裝目錄中找到[!INCLUDE[Compact](~/includes/compact-md.md)]C 磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="f2196-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="f2196-119">一般而言，您可使用的最新版本[!INCLUDE[Compact](~/includes/compact-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f2196-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2196-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2196-120">See Also</span></span>  
 [<span data-ttu-id="f2196-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="f2196-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="f2196-122">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="f2196-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="f2196-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="f2196-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [<span data-ttu-id="f2196-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="f2196-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
