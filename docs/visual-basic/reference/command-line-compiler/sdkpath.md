---
title: /sdkpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- /sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 876922385124db3e8db12c93c75194da83d2526c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="sdkpath"></a><span data-ttu-id="4fe09-102">/sdkpath</span><span class="sxs-lookup"><span data-stu-id="4fe09-102">/sdkpath</span></span>
<span data-ttu-id="4fe09-103">指定 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。</span><span class="sxs-lookup"><span data-stu-id="4fe09-103">Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe09-104">語法</span><span class="sxs-lookup"><span data-stu-id="4fe09-104">Syntax</span></span>  
  
```  
/sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="4fe09-105">引數</span><span class="sxs-lookup"><span data-stu-id="4fe09-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="4fe09-106">包含要用於編譯的 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的版本的目錄。</span><span class="sxs-lookup"><span data-stu-id="4fe09-106">The directory containing the versions of Mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="4fe09-107">未驗證此路徑，直到它載入。</span><span class="sxs-lookup"><span data-stu-id="4fe09-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="4fe09-108">將目錄名稱括在引號 ("") 如果包含空格。</span><span class="sxs-lookup"><span data-stu-id="4fe09-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fe09-109">備註</span><span class="sxs-lookup"><span data-stu-id="4fe09-109">Remarks</span></span>  
 <span data-ttu-id="4fe09-110">此選項會告知[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器，從非預設位置載入 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的檔案。</span><span class="sxs-lookup"><span data-stu-id="4fe09-110">This option tells the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to load the Mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="4fe09-111">`/sdkpath`選項設計用來搭配[/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)。</span><span class="sxs-lookup"><span data-stu-id="4fe09-111">The `/sdkpath` option was designed to be used with [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="4fe09-112">[!INCLUDE[Compact](~/includes/compact-md.md)]會使用不同版本的支援程式庫，以避免使用的類型和語言功能的裝置上找不到。</span><span class="sxs-lookup"><span data-stu-id="4fe09-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4fe09-113">`/sdkpath`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。</span><span class="sxs-lookup"><span data-stu-id="4fe09-113">The `/sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="4fe09-114">`/sdkpath`時設定選項[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]裝置專案載入。</span><span class="sxs-lookup"><span data-stu-id="4fe09-114">The `/sdkpath` option is set when a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="4fe09-115">您可以指定編譯器應該使用編譯 Visual Basic 執行階段程式庫的參考不`/vbruntime`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="4fe09-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `/vbruntime` compiler option.</span></span> <span data-ttu-id="4fe09-116">如需詳細資訊，請參閱[/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)。</span><span class="sxs-lookup"><span data-stu-id="4fe09-116">For more information, see [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fe09-117">範例</span><span class="sxs-lookup"><span data-stu-id="4fe09-117">Example</span></span>  
 <span data-ttu-id="4fe09-118">下列程式碼編譯`Myfile.vb`與[!INCLUDE[Compact](~/includes/compact-md.md)]，使用 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的版本中的預設安裝目錄中找到[!INCLUDE[Compact](~/includes/compact-md.md)]C 磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="4fe09-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="4fe09-119">一般而言，您可使用的最新版本[!INCLUDE[Compact](~/includes/compact-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4fe09-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fe09-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fe09-120">See Also</span></span>  
 [<span data-ttu-id="4fe09-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="4fe09-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="4fe09-122">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="4fe09-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="4fe09-123">/netcf</span><span class="sxs-lookup"><span data-stu-id="4fe09-123">/netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [<span data-ttu-id="4fe09-124">/vbruntime</span><span class="sxs-lookup"><span data-stu-id="4fe09-124">/vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
