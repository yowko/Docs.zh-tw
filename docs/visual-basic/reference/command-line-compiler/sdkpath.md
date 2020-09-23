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
ms.openlocfilehash: 18bf22861c1cbc3a37ef917b421491c2d01efba8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085109"
---
# <a name="-sdkpath"></a><span data-ttu-id="2b663-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="2b663-102">-sdkpath</span></span>

<span data-ttu-id="2b663-103">指定 mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。</span><span class="sxs-lookup"><span data-stu-id="2b663-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b663-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b663-104">Syntax</span></span>  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="2b663-105">引數</span><span class="sxs-lookup"><span data-stu-id="2b663-105">Arguments</span></span>  

 `path`  
 <span data-ttu-id="2b663-106">包含 mscorlib.dll 版本的目錄，以及用於編譯的 Microsoft.VisualBasic.dll。</span><span class="sxs-lookup"><span data-stu-id="2b663-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="2b663-107">在載入之前，不會驗證此路徑。</span><span class="sxs-lookup"><span data-stu-id="2b663-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="2b663-108">以引號括住目錄名稱 ( "" ) 如果它包含空格。</span><span class="sxs-lookup"><span data-stu-id="2b663-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b663-109">備註</span><span class="sxs-lookup"><span data-stu-id="2b663-109">Remarks</span></span>  

 <span data-ttu-id="2b663-110">此選項會指示 Visual Basic 編譯器從非預設位置載入 mscorlib.dll 和 Microsoft.VisualBasic.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="2b663-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="2b663-111">此 `-sdkpath` 選項的設計目的是要搭配 [-netcf](netcf.md)使用。</span><span class="sxs-lookup"><span data-stu-id="2b663-111">The `-sdkpath` option was designed to be used with [-netcf](netcf.md).</span></span> <span data-ttu-id="2b663-112">.NET Compact Framework 使用這些支援程式庫的不同版本，以避免使用在裝置上找不到的類型和語言功能。</span><span class="sxs-lookup"><span data-stu-id="2b663-112">The .NET Compact Framework uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b663-113">`-sdkpath`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="2b663-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="2b663-114">`-sdkpath`載入 Visual Basic 裝置專案時，會設定此選項。</span><span class="sxs-lookup"><span data-stu-id="2b663-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="2b663-115">您可以使用編譯器選項，指定編譯器不需要參考 Visual Basic 執行時間程式庫 `-vbruntime` 。</span><span class="sxs-lookup"><span data-stu-id="2b663-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="2b663-116">如需詳細資訊，請參閱 [-vbruntime](vbruntime.md)。</span><span class="sxs-lookup"><span data-stu-id="2b663-116">For more information, see [-vbruntime](vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b663-117">範例</span><span class="sxs-lookup"><span data-stu-id="2b663-117">Example</span></span>  

 <span data-ttu-id="2b663-118">下列程式碼會 `Myfile.vb` 使用 .NET Compact Framework，並使用在 C 磁片磁碟機上 .NET Compact Framework 的預設安裝目錄中找到的 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的版本進行編譯。</span><span class="sxs-lookup"><span data-stu-id="2b663-118">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="2b663-119">一般來說，您會使用最新版本的 .NET Compact Framework。</span><span class="sxs-lookup"><span data-stu-id="2b663-119">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b663-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b663-120">See also</span></span>

- [<span data-ttu-id="2b663-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="2b663-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="2b663-122">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="2b663-122">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="2b663-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="2b663-123">-netcf</span></span>](netcf.md)
- [<span data-ttu-id="2b663-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="2b663-124">-vbruntime</span></span>](vbruntime.md)
