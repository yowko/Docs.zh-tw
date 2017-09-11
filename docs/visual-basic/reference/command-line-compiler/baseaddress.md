---
title: "/baseaddress |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
dev_langs:
- VB
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: 16
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
ms.openlocfilehash: 5687f119a57e0e54eca4df8f91fdf5e8b2775f82
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="baseaddress"></a><span data-ttu-id="acf4b-102">/baseaddress</span><span class="sxs-lookup"><span data-stu-id="acf4b-102">/baseaddress</span></span>
<span data-ttu-id="acf4b-103">建立 DLL 時，請指定預設的基底位址。</span><span class="sxs-lookup"><span data-stu-id="acf4b-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf4b-104">語法</span><span class="sxs-lookup"><span data-stu-id="acf4b-104">Syntax</span></span>  
  
```  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="acf4b-105">引數</span><span class="sxs-lookup"><span data-stu-id="acf4b-105">Arguments</span></span>  
  
|<span data-ttu-id="acf4b-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="acf4b-106">Term</span></span>|<span data-ttu-id="acf4b-107">定義</span><span class="sxs-lookup"><span data-stu-id="acf4b-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="acf4b-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="acf4b-108">Required.</span></span> <span data-ttu-id="acf4b-109">DLL 的基底位址。</span><span class="sxs-lookup"><span data-stu-id="acf4b-109">The base address for the DLL.</span></span> <span data-ttu-id="acf4b-110">此位址必須指定為十六進位數字。</span><span class="sxs-lookup"><span data-stu-id="acf4b-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acf4b-111">備註</span><span class="sxs-lookup"><span data-stu-id="acf4b-111">Remarks</span></span>  
 <span data-ttu-id="acf4b-112">DLL 預設基底位址由設定[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="acf4b-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span>  
  
 <span data-ttu-id="acf4b-113">請注意，此位址中的低序位字會四捨五入。</span><span class="sxs-lookup"><span data-stu-id="acf4b-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="acf4b-114">例如，如果您指定的是 0x11110001，會捨入為 0x11110000。</span><span class="sxs-lookup"><span data-stu-id="acf4b-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="acf4b-115">若要完成簽署程序的 DLL，使用`–R`強式命名的工具 (Sn.exe) 選項。</span><span class="sxs-lookup"><span data-stu-id="acf4b-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="acf4b-116">如果目標不是 DLL，則會忽略這個選項。</span><span class="sxs-lookup"><span data-stu-id="acf4b-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="acf4b-117">在 Visual Studio IDE 中設定 /baseaddress</span><span class="sxs-lookup"><span data-stu-id="acf4b-117">To set /baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="acf4b-118">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="acf4b-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="acf4b-119">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="acf4b-119">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="acf4b-120">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="acf4b-120">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="acf4b-121">2.按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="acf4b-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="acf4b-122">3.按一下 [ **進階**]。</span><span class="sxs-lookup"><span data-stu-id="acf4b-122">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="acf4b-123">4.修改中的值**DLL 基底位址︰**方塊。</span><span class="sxs-lookup"><span data-stu-id="acf4b-123">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="acf4b-124">**注意︰** **DLL 基底位址︰**方塊是唯讀的除非目標是 DLL。</span><span class="sxs-lookup"><span data-stu-id="acf4b-124">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="acf4b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acf4b-125">See Also</span></span>  
 <span data-ttu-id="acf4b-126">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="acf4b-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="acf4b-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="acf4b-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="acf4b-128"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="acf4b-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="acf4b-129"> [Sn.exe （強式名稱工具）](https://msdn.microsoft.com/library/k5b5tt23)</span><span class="sxs-lookup"><span data-stu-id="acf4b-129"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23)</span></span>
