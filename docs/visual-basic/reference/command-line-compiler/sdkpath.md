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
ms.openlocfilehash: 46cec7ac3cb78c4fc97e299535f9085eff6daeff
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004688"
---
# <a name="-sdkpath"></a><span data-ttu-id="b2d2c-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="b2d2c-102">-sdkpath</span></span>
<span data-ttu-id="b2d2c-103">指定 mscorlib.dll 和 Microsoft 的位置。</span><span class="sxs-lookup"><span data-stu-id="b2d2c-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2d2c-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2d2c-104">Syntax</span></span>  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="b2d2c-105">引數</span><span class="sxs-lookup"><span data-stu-id="b2d2c-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="b2d2c-106">包含要用於編譯之 mscorlib.dll 和 node.js 版本的目錄。</span><span class="sxs-lookup"><span data-stu-id="b2d2c-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="b2d2c-107">此路徑要等到載入後才會驗證。</span><span class="sxs-lookup"><span data-stu-id="b2d2c-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="b2d2c-108">如果目錄名稱包含空格，請將其括在引號（""）中。</span><span class="sxs-lookup"><span data-stu-id="b2d2c-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2d2c-109">備註</span><span class="sxs-lookup"><span data-stu-id="b2d2c-109">Remarks</span></span>  
 <span data-ttu-id="b2d2c-110">此選項會告訴 Visual Basic 編譯器從非預設位置載入 mscorlib.dll 和 Microsoft..。</span><span class="sxs-lookup"><span data-stu-id="b2d2c-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="b2d2c-111">選項`-sdkpath`的設計目的是要搭配[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)使用。</span><span class="sxs-lookup"><span data-stu-id="b2d2c-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="b2d2c-112">.NET Compact Framework 會使用這些支援程式庫的不同版本，以避免使用在裝置上找不到的類型和語言功能。</span><span class="sxs-lookup"><span data-stu-id="b2d2c-112">The .NET Compact Framework uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2d2c-113">此`-sdkpath`選項無法在 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="b2d2c-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="b2d2c-114">當`-sdkpath`載入 Visual Basic 裝置專案時，就會設定此選項。</span><span class="sxs-lookup"><span data-stu-id="b2d2c-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="b2d2c-115">您可以指定編譯器在不參考 Visual Basic 執行時間程式庫的情況下，使用`-vbruntime`編譯器選項進行編譯。</span><span class="sxs-lookup"><span data-stu-id="b2d2c-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="b2d2c-116">如需詳細資訊，請參閱[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)。</span><span class="sxs-lookup"><span data-stu-id="b2d2c-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2d2c-117">範例</span><span class="sxs-lookup"><span data-stu-id="b2d2c-117">Example</span></span>  
 <span data-ttu-id="b2d2c-118">下列程式碼會`Myfile.vb`使用 .NET Compact Framework 進行編譯，其方式是在 C 磁片磁碟機上 .NET Compact Framework 的預設安裝目錄中找到 Mscorlib.dll 和 Microsoft 的版本。</span><span class="sxs-lookup"><span data-stu-id="b2d2c-118">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="b2d2c-119">一般來說，您會使用最新版本的 .NET Compact Framework。</span><span class="sxs-lookup"><span data-stu-id="b2d2c-119">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2d2c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2d2c-120">See also</span></span>

- [<span data-ttu-id="b2d2c-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="b2d2c-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="b2d2c-122">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="b2d2c-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="b2d2c-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="b2d2c-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [<span data-ttu-id="b2d2c-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="b2d2c-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
