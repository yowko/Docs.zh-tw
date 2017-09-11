---
title: "/codepage (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6f4919bc4fc8eda700edbd80fead5b5d9fe0dba1
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="codepage-visual-basic"></a><span data-ttu-id="fc665-102">/codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc665-102">/codepage (Visual Basic)</span></span>
<span data-ttu-id="fc665-103">指定編譯過程中所有原始程式碼檔使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="fc665-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc665-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc665-104">Syntax</span></span>  
  
```  
/codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="fc665-105">引數</span><span class="sxs-lookup"><span data-stu-id="fc665-105">Arguments</span></span>  
  
|<span data-ttu-id="fc665-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="fc665-106">Term</span></span>|<span data-ttu-id="fc665-107">定義</span><span class="sxs-lookup"><span data-stu-id="fc665-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="fc665-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="fc665-108">Required.</span></span> <span data-ttu-id="fc665-109">編譯器會使用所指定的字碼頁`id`解譯原始程式檔的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="fc665-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc665-110">備註</span><span class="sxs-lookup"><span data-stu-id="fc665-110">Remarks</span></span>  
 <span data-ttu-id="fc665-111">若要編譯原始程式碼與特定的編碼方式儲存，您可以使用`/codepage`來指定應該使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="fc665-111">To compile source code saved with a specific encoding, you can use `/codepage` to specify which code page should be used.</span></span> <span data-ttu-id="fc665-112">`/codepage`選項套用至所有您所編譯的原始程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="fc665-112">The `/codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="fc665-113">如需詳細資訊，請參閱[.NET Framework 中的字元編碼](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9)。</span><span class="sxs-lookup"><span data-stu-id="fc665-113">For more information, see [Character Encoding in the .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="fc665-114">`/codepage`選項不需要簽章中使用目前的 ANSI 字碼頁、 Unicode 或 utf-8 格式儲存的原始程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="fc665-114">The `/codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="fc665-115">儲存所有原始程式碼檔案與目前的 ANSI 字碼頁，根據預設，除非使用者指定另一個編碼**編碼**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fc665-115"> saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="fc665-116">使用**編碼**對話方塊來開啟不同的字碼頁所儲存的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="fc665-116"> uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc665-117">`/codepage`選項不可以從[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]開發環境，它才可使用從命令列進行編譯。</span><span class="sxs-lookup"><span data-stu-id="fc665-117">The `/codepage` option is not available from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc665-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc665-118">See Also</span></span>  
 [<span data-ttu-id="fc665-119">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="fc665-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
