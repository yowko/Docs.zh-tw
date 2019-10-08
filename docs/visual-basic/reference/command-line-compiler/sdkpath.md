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
# <a name="-sdkpath"></a><span data-ttu-id="019c0-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="019c0-102">-sdkpath</span></span>
<span data-ttu-id="019c0-103">指定 mscorlib.dll 和 Microsoft 的位置。</span><span class="sxs-lookup"><span data-stu-id="019c0-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="019c0-104">語法</span><span class="sxs-lookup"><span data-stu-id="019c0-104">Syntax</span></span>  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="019c0-105">引數</span><span class="sxs-lookup"><span data-stu-id="019c0-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="019c0-106">包含要用於編譯之 mscorlib.dll 和 node.js 版本的目錄。</span><span class="sxs-lookup"><span data-stu-id="019c0-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="019c0-107">此路徑要等到載入後才會驗證。</span><span class="sxs-lookup"><span data-stu-id="019c0-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="019c0-108">如果目錄名稱包含空格，請將其括在引號（""）中。</span><span class="sxs-lookup"><span data-stu-id="019c0-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="019c0-109">備註</span><span class="sxs-lookup"><span data-stu-id="019c0-109">Remarks</span></span>  
 <span data-ttu-id="019c0-110">此選項會告訴 Visual Basic 編譯器從非預設位置載入 mscorlib.dll 和 Microsoft..。</span><span class="sxs-lookup"><span data-stu-id="019c0-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="019c0-111">@No__t-0 選項是設計來搭配[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)使用。</span><span class="sxs-lookup"><span data-stu-id="019c0-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="019c0-112">.NET Compact Framework 會使用這些支援程式庫的不同版本，以避免使用在裝置上找不到的類型和語言功能。</span><span class="sxs-lookup"><span data-stu-id="019c0-112">The .NET Compact Framework uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="019c0-113">@No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="019c0-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="019c0-114">載入 Visual Basic 裝置專案時，會設定 `-sdkpath` 選項。</span><span class="sxs-lookup"><span data-stu-id="019c0-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="019c0-115">您可以指定編譯器不需要使用 `-vbruntime` 編譯器選項來進行 Visual Basic 執行時間程式庫的參考編譯。</span><span class="sxs-lookup"><span data-stu-id="019c0-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="019c0-116">如需詳細資訊，請參閱[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)。</span><span class="sxs-lookup"><span data-stu-id="019c0-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="019c0-117">範例</span><span class="sxs-lookup"><span data-stu-id="019c0-117">Example</span></span>  
 <span data-ttu-id="019c0-118">下列程式碼會使用在 C 磁片磁碟機上 .NET Compact Framework 的預設安裝目錄中找到的 Mscorlib.dll 和 default.aspx 版本，搭配 .NET Compact Framework 來編譯 `Myfile.vb`。</span><span class="sxs-lookup"><span data-stu-id="019c0-118">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="019c0-119">一般來說，您會使用最新版本的 .NET Compact Framework。</span><span class="sxs-lookup"><span data-stu-id="019c0-119">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="019c0-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="019c0-120">See also</span></span>

- [<span data-ttu-id="019c0-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="019c0-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="019c0-122">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="019c0-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="019c0-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="019c0-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [<span data-ttu-id="019c0-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="019c0-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
