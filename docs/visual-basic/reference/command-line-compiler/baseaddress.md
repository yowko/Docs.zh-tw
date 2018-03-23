---
title: -baseaddress
ms.date: 08/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3abe566e7a32a0b350a4f483df5c77fa4d003367
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-baseaddress"></a><span data-ttu-id="37e2b-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="37e2b-102">-baseaddress</span></span>
<span data-ttu-id="37e2b-103">建立 DLL 時，請指定預設基底地址。</span><span class="sxs-lookup"><span data-stu-id="37e2b-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37e2b-104">語法</span><span class="sxs-lookup"><span data-stu-id="37e2b-104">Syntax</span></span>  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="37e2b-105">引數</span><span class="sxs-lookup"><span data-stu-id="37e2b-105">Arguments</span></span>  
  
|<span data-ttu-id="37e2b-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="37e2b-106">Term</span></span>|<span data-ttu-id="37e2b-107">定義</span><span class="sxs-lookup"><span data-stu-id="37e2b-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="37e2b-108">必要。</span><span class="sxs-lookup"><span data-stu-id="37e2b-108">Required.</span></span> <span data-ttu-id="37e2b-109">DLL 的基底位址。</span><span class="sxs-lookup"><span data-stu-id="37e2b-109">The base address for the DLL.</span></span> <span data-ttu-id="37e2b-110">此位址必須指定為十六進位數字。</span><span class="sxs-lookup"><span data-stu-id="37e2b-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37e2b-111">備註</span><span class="sxs-lookup"><span data-stu-id="37e2b-111">Remarks</span></span>  
 <span data-ttu-id="37e2b-112">DLL 預設基底地址由設定[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="37e2b-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="37e2b-113">請注意這個位址的低序位字會捨入。</span><span class="sxs-lookup"><span data-stu-id="37e2b-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="37e2b-114">例如，如果您指定的是 0x11110001，它會捨入到 0x11110000。</span><span class="sxs-lookup"><span data-stu-id="37e2b-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="37e2b-115">若要完成 DLL 的簽章的程序，使用`–R`強式命名的工具 (Sn.exe) 選項。</span><span class="sxs-lookup"><span data-stu-id="37e2b-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="37e2b-116">如果目標不是 DLL，就會忽略此選項。</span><span class="sxs-lookup"><span data-stu-id="37e2b-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="37e2b-117">在 Visual Studio IDE 中設定-baseaddress</span><span class="sxs-lookup"><span data-stu-id="37e2b-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="37e2b-118">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="37e2b-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="37e2b-119">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="37e2b-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="37e2b-120">2.按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="37e2b-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="37e2b-121">3.按一下 [ **進階**]。</span><span class="sxs-lookup"><span data-stu-id="37e2b-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="37e2b-122">4.修改中的值**DLL 基底位址：**方塊。</span><span class="sxs-lookup"><span data-stu-id="37e2b-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="37e2b-123">**注意：** **DLL 基底位址：**方塊是唯讀的除非目標是 DLL。</span><span class="sxs-lookup"><span data-stu-id="37e2b-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37e2b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37e2b-124">See Also</span></span>  
 [<span data-ttu-id="37e2b-125">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="37e2b-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="37e2b-126">-目標 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37e2b-126">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="37e2b-127">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="37e2b-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="37e2b-128">[Sn.exe （強式名稱工具）][Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="37e2b-128">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
