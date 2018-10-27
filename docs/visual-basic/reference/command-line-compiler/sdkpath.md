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
ms.openlocfilehash: bf665082f079901ec45122ce7797090b7519fafe
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50046795"
---
# <a name="-sdkpath"></a><span data-ttu-id="920e9-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="920e9-102">-sdkpath</span></span>
<span data-ttu-id="920e9-103">指定 mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。</span><span class="sxs-lookup"><span data-stu-id="920e9-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="920e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="920e9-104">Syntax</span></span>  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="920e9-105">引數</span><span class="sxs-lookup"><span data-stu-id="920e9-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="920e9-106">包含 mscorlib.dll 和 Microsoft.VisualBasic.dll 編譯来使用的版本的目錄。</span><span class="sxs-lookup"><span data-stu-id="920e9-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="920e9-107">此路徑未驗證之前載入。</span><span class="sxs-lookup"><span data-stu-id="920e9-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="920e9-108">將目錄名稱括在引號 ("") 如果它包含空格。</span><span class="sxs-lookup"><span data-stu-id="920e9-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="920e9-109">備註</span><span class="sxs-lookup"><span data-stu-id="920e9-109">Remarks</span></span>  
 <span data-ttu-id="920e9-110">此選項會告訴 Visual Basic 編譯器，從非預設位置載入 mscorlib.dll 和 Microsoft.VisualBasic.dll 的檔案。</span><span class="sxs-lookup"><span data-stu-id="920e9-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="920e9-111">`-sdkpath`選項設計來搭配[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)。</span><span class="sxs-lookup"><span data-stu-id="920e9-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="920e9-112">[!INCLUDE[Compact](~/includes/compact-md.md)]會使用不同版本的支援程式庫，以避免使用的類型和裝置上找不到的語言功能。</span><span class="sxs-lookup"><span data-stu-id="920e9-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="920e9-113">`-sdkpath`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。</span><span class="sxs-lookup"><span data-stu-id="920e9-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="920e9-114">`-sdkpath` Visual Basic 裝置專案載入時，設定選項。</span><span class="sxs-lookup"><span data-stu-id="920e9-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="920e9-115">您可以指定編譯器應使用編譯 Visual Basic 執行階段程式庫參考`-vbruntime`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="920e9-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="920e9-116">如需詳細資訊，請參閱 < [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)。</span><span class="sxs-lookup"><span data-stu-id="920e9-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="920e9-117">範例</span><span class="sxs-lookup"><span data-stu-id="920e9-117">Example</span></span>  
 <span data-ttu-id="920e9-118">下列程式碼會編譯`Myfile.vb`具有[!INCLUDE[Compact](~/includes/compact-md.md)]，使用 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的新版的預設安裝目錄中找到[!INCLUDE[Compact](~/includes/compact-md.md)]C 磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="920e9-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="920e9-119">一般而言，您會使用最新版本的[!INCLUDE[Compact](~/includes/compact-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="920e9-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="920e9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="920e9-120">See Also</span></span>  
 [<span data-ttu-id="920e9-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="920e9-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="920e9-122">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="920e9-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="920e9-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="920e9-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [<span data-ttu-id="920e9-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="920e9-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
