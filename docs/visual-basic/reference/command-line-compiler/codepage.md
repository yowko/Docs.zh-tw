---
title: /codepage (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 609373ed0e58eec86a703f33d48d31e27b0b7e3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="codepage-visual-basic"></a><span data-ttu-id="a042e-102">/codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a042e-102">/codepage (Visual Basic)</span></span>
<span data-ttu-id="a042e-103">指定編譯過程中所有原始程式碼檔使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="a042e-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a042e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a042e-104">Syntax</span></span>  
  
```  
/codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="a042e-105">引數</span><span class="sxs-lookup"><span data-stu-id="a042e-105">Arguments</span></span>  
  
|<span data-ttu-id="a042e-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="a042e-106">Term</span></span>|<span data-ttu-id="a042e-107">定義</span><span class="sxs-lookup"><span data-stu-id="a042e-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="a042e-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="a042e-108">Required.</span></span> <span data-ttu-id="a042e-109">編譯器會使用所指定的字碼頁`id`解譯原始程式檔的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="a042e-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a042e-110">備註</span><span class="sxs-lookup"><span data-stu-id="a042e-110">Remarks</span></span>  
 <span data-ttu-id="a042e-111">若要編譯原始程式碼，以特定編碼方式儲存，您可以使用`/codepage`來指定應該使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="a042e-111">To compile source code saved with a specific encoding, you can use `/codepage` to specify which code page should be used.</span></span> <span data-ttu-id="a042e-112">`/codepage`選項適用於您所編譯的所有原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="a042e-112">The `/codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="a042e-113">如需詳細資訊，請參閱[字元編碼方式在.NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9)。</span><span class="sxs-lookup"><span data-stu-id="a042e-113">For more information, see [Character Encoding in the .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="a042e-114">`/codepage`如果原始程式檔儲存具有簽章中使用目前的 ANSI 字碼頁、 Unicode 或 utf-8，則不需要選項。</span><span class="sxs-lookup"><span data-stu-id="a042e-114">The `/codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="a042e-115">儲存所有原始程式碼檔案與目前的 ANSI 字碼頁，根據預設，除非使用者另外指定其他編碼方式在**編碼** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a042e-115"> saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="a042e-116">使用**編碼**對話方塊來開啟原始程式碼檔使用不同的字碼頁儲存。</span><span class="sxs-lookup"><span data-stu-id="a042e-116"> uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a042e-117">`/codepage`選項不是可從[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]開發環境中，只有在從命令列編譯時，它是可用。</span><span class="sxs-lookup"><span data-stu-id="a042e-117">The `/codepage` option is not available from within the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a042e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a042e-118">See Also</span></span>  
 [<span data-ttu-id="a042e-119">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="a042e-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
