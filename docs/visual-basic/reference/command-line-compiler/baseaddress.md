---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: c794d1fc1c9d20e22ffa747e3175c846341ad8ad
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097757"
---
# <a name="-baseaddress"></a><span data-ttu-id="0e67d-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="0e67d-102">-baseaddress</span></span>

<span data-ttu-id="0e67d-103">指定建立 DLL 時的預設基底位址。</span><span class="sxs-lookup"><span data-stu-id="0e67d-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e67d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e67d-104">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="0e67d-105">引數</span><span class="sxs-lookup"><span data-stu-id="0e67d-105">Arguments</span></span>  
  
|<span data-ttu-id="0e67d-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="0e67d-106">Term</span></span>|<span data-ttu-id="0e67d-107">定義</span><span class="sxs-lookup"><span data-stu-id="0e67d-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="0e67d-108">必要。</span><span class="sxs-lookup"><span data-stu-id="0e67d-108">Required.</span></span> <span data-ttu-id="0e67d-109">DLL 的基底位址。</span><span class="sxs-lookup"><span data-stu-id="0e67d-109">The base address for the DLL.</span></span> <span data-ttu-id="0e67d-110">此位址必須指定為十六進位數位。</span><span class="sxs-lookup"><span data-stu-id="0e67d-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e67d-111">備註</span><span class="sxs-lookup"><span data-stu-id="0e67d-111">Remarks</span></span>  

 <span data-ttu-id="0e67d-112">DLL 的預設基底位址是由 .NET Framework 設定。</span><span class="sxs-lookup"><span data-stu-id="0e67d-112">The default base address for a DLL is set by the .NET Framework.</span></span>  
  
 <span data-ttu-id="0e67d-113">請注意，此位址中的低序位單字會四捨五入。</span><span class="sxs-lookup"><span data-stu-id="0e67d-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="0e67d-114">例如，如果您指定0x11110001，則會將它四捨五入為0x11110000。</span><span class="sxs-lookup"><span data-stu-id="0e67d-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="0e67d-115">若要完成 DLL 的簽署程式，請使用 `–R` 強式命名工具的選項 ( # A0) 。</span><span class="sxs-lookup"><span data-stu-id="0e67d-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="0e67d-116">如果目標不是 DLL，則會忽略這個選項。</span><span class="sxs-lookup"><span data-stu-id="0e67d-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="0e67d-117">若要在 Visual Studio IDE 中設定-baseaddress</span><span class="sxs-lookup"><span data-stu-id="0e67d-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="0e67d-118">1. 在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="0e67d-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0e67d-119">按一下 [專案] 功能表上的 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0e67d-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="0e67d-120">2. 按一下 [ **編譯** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0e67d-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="0e67d-121">3. 按一下 [ **Advanced**]。</span><span class="sxs-lookup"><span data-stu-id="0e67d-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="0e67d-122">4. 修改 [ **DLL 基底位址：** ] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="0e67d-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="0e67d-123">**注意：**      除非目標是 DLL，否則 **DLL 基底位址：** box 是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="0e67d-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e67d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e67d-124">See also</span></span>

- [<span data-ttu-id="0e67d-125">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="0e67d-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0e67d-126">-目標 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="0e67d-126">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="0e67d-127">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="0e67d-127">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- <span data-ttu-id="0e67d-128">[Sn.exe (強式名稱工具) ](../../../framework/tools/sn-exe-strong-name-tool.md)) </span><span class="sxs-lookup"><span data-stu-id="0e67d-128">[Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
