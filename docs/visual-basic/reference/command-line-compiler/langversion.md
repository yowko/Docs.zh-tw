---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: db2cb1eb107973e9ce60ecb0d669c677d4fa2c51
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839715"
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="61e91-102">-langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61e91-102">-langversion (Visual Basic)</span></span>
<span data-ttu-id="61e91-103">可讓編譯器接受包含在指定的 Visual Basic 語言版本的語法。</span><span class="sxs-lookup"><span data-stu-id="61e91-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61e91-104">語法</span><span class="sxs-lookup"><span data-stu-id="61e91-104">Syntax</span></span>  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="61e91-105">引數</span><span class="sxs-lookup"><span data-stu-id="61e91-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="61e91-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="61e91-106">Required.</span></span> <span data-ttu-id="61e91-107">要在編譯期間使用的語言版本。</span><span class="sxs-lookup"><span data-stu-id="61e91-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="61e91-108">接受的值為`9`， `10`， `11`， `12`， `14`， `15`， `15.3`， `15.5`，`default`和`latest`。</span><span class="sxs-lookup"><span data-stu-id="61e91-108">Accepted values are `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` and `latest`.</span></span>

 <span data-ttu-id="61e91-109">任何整數也可以指定使用`.0`是次要版本，例如`11.0`。</span><span class="sxs-lookup"><span data-stu-id="61e91-109">Any of the whole numbers may also be specified using `.0` as the minor version, for example, `11.0`.</span></span>

 <span data-ttu-id="61e91-110">您可以看到所有的可能值的清單，藉由指定`-langversion:?`命令列上。</span><span class="sxs-lookup"><span data-stu-id="61e91-110">You can see the list of all possible values by specifying `-langversion:?` on the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61e91-111">備註</span><span class="sxs-lookup"><span data-stu-id="61e91-111">Remarks</span></span>  
 <span data-ttu-id="61e91-112">`-langversion`選項指定何種編譯器接受的語法。</span><span class="sxs-lookup"><span data-stu-id="61e91-112">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="61e91-113">例如，如果您指定的語言版本 9.0，編譯器會產生僅適用於 10.0 版及更新版本的語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="61e91-113">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="61e91-114">當您開發應用程式不同版本為目標的.NET framework 時，您可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="61e91-114">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="61e91-115">例如，如果您的目標.NET Framework 3.5，您可以使用此選項以確保不會使用從 10.0 版的語言的語法。</span><span class="sxs-lookup"><span data-stu-id="61e91-115">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="61e91-116">您可以設定`-langversion`直接只能藉由使用命令列。</span><span class="sxs-lookup"><span data-stu-id="61e91-116">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="61e91-117">如需詳細資訊，請參閱[以特定的 .NET Framework 版本為目標](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)。</span><span class="sxs-lookup"><span data-stu-id="61e91-117">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="61e91-118">範例</span><span class="sxs-lookup"><span data-stu-id="61e91-118">Example</span></span>  
 <span data-ttu-id="61e91-119">下列程式碼編譯`sample.vb`的 Visual Basic 9.0。</span><span class="sxs-lookup"><span data-stu-id="61e91-119">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="61e91-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61e91-120">See also</span></span>

- [<span data-ttu-id="61e91-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="61e91-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="61e91-122">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="61e91-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="61e91-123">以特定的 .NET Framework 版本為目標</span><span class="sxs-lookup"><span data-stu-id="61e91-123">Targeting a Specific .NET Framework Version</span></span>](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
