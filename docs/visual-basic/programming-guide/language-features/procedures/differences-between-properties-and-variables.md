---
title: 屬性和變數之間的差異
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
ms.openlocfilehash: 162bd71eaebdf55f6be89e0c5dce7acc1b975d79
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403300"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a><span data-ttu-id="2306c-102">Visual Basic 中屬性和變數的差別</span><span class="sxs-lookup"><span data-stu-id="2306c-102">Differences Between Properties and Variables in Visual Basic</span></span>
<span data-ttu-id="2306c-103">變數和屬性都代表您可以存取的值。</span><span class="sxs-lookup"><span data-stu-id="2306c-103">Variables and properties both represent values that you can access.</span></span> <span data-ttu-id="2306c-104">不過，儲存體和實作為差異。</span><span class="sxs-lookup"><span data-stu-id="2306c-104">However, there are differences in storage and implementation.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="2306c-105">變數</span><span class="sxs-lookup"><span data-stu-id="2306c-105">Variables</span></span>  
 <span data-ttu-id="2306c-106">*變數*會直接對應到記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="2306c-106">A *variable* corresponds directly to a memory location.</span></span> <span data-ttu-id="2306c-107">您可以使用單一宣告語句來定義變數。</span><span class="sxs-lookup"><span data-stu-id="2306c-107">You define a variable with a single declaration statement.</span></span> <span data-ttu-id="2306c-108">變數可以是在程式內定義的*區域變數*，而且只能在該程式內使用，或者可以是在模組、類別或結構中定義，但不在任何程式內的*成員變數*。</span><span class="sxs-lookup"><span data-stu-id="2306c-108">A variable can be a *local variable*, defined inside a procedure and available only within that procedure, or it can be a *member variable*, defined in a module, class, or structure but not inside any procedure.</span></span> <span data-ttu-id="2306c-109">成員變數也稱為*欄位*。</span><span class="sxs-lookup"><span data-stu-id="2306c-109">A member variable is also called a *field*.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2306c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2306c-110">Properties</span></span>  
 <span data-ttu-id="2306c-111">「*屬性*」（property）是在模組、類別或結構上定義的資料元素。</span><span class="sxs-lookup"><span data-stu-id="2306c-111">A *property* is a data element defined on a module, class, or structure.</span></span> <span data-ttu-id="2306c-112">您可以使用和語句之間的程式碼區塊來定義屬性 `Property` `End Property` 。</span><span class="sxs-lookup"><span data-stu-id="2306c-112">You define a property with a code block between the `Property` and `End Property` statements.</span></span> <span data-ttu-id="2306c-113">程式碼區塊包含程式 `Get` 、程式 `Set` 或兩者。</span><span class="sxs-lookup"><span data-stu-id="2306c-113">The code block contains a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="2306c-114">這些程式稱為*屬性程式*或*屬性存取*子。</span><span class="sxs-lookup"><span data-stu-id="2306c-114">These procedures are called *property procedures* or *property accessors*.</span></span> <span data-ttu-id="2306c-115">除了抓取或儲存屬性的值之外，它們也可以執行自訂動作，例如更新存取計數器。</span><span class="sxs-lookup"><span data-stu-id="2306c-115">In addition to retrieving or storing the property's value, they can also perform custom actions, such as updating an access counter.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="2306c-116">差異</span><span class="sxs-lookup"><span data-stu-id="2306c-116">Differences</span></span>  
 <span data-ttu-id="2306c-117">下表顯示變數和屬性之間的一些重要差異。</span><span class="sxs-lookup"><span data-stu-id="2306c-117">The following table shows some important differences between variables and properties.</span></span>  
  
|<span data-ttu-id="2306c-118">差異點</span><span class="sxs-lookup"><span data-stu-id="2306c-118">Point of difference</span></span>|<span data-ttu-id="2306c-119">變數</span><span class="sxs-lookup"><span data-stu-id="2306c-119">Variable</span></span>|<span data-ttu-id="2306c-120">屬性</span><span class="sxs-lookup"><span data-stu-id="2306c-120">Property</span></span>|  
|-------------------------|--------------|--------------|  
|<span data-ttu-id="2306c-121">宣告</span><span class="sxs-lookup"><span data-stu-id="2306c-121">Declaration</span></span>|<span data-ttu-id="2306c-122">單一宣告語句</span><span class="sxs-lookup"><span data-stu-id="2306c-122">Single declaration statement</span></span>|<span data-ttu-id="2306c-123">程式碼區塊中的一連串語句</span><span class="sxs-lookup"><span data-stu-id="2306c-123">Series of statements in a code block</span></span>|  
|<span data-ttu-id="2306c-124">實作</span><span class="sxs-lookup"><span data-stu-id="2306c-124">Implementation</span></span>|<span data-ttu-id="2306c-125">單一儲存位置</span><span class="sxs-lookup"><span data-stu-id="2306c-125">Single storage location</span></span>|<span data-ttu-id="2306c-126">可執行程式碼（屬性程式）</span><span class="sxs-lookup"><span data-stu-id="2306c-126">Executable code (property procedures)</span></span>|  
|<span data-ttu-id="2306c-127">儲存體</span><span class="sxs-lookup"><span data-stu-id="2306c-127">Storage</span></span>|<span data-ttu-id="2306c-128">直接與變數的值相關聯</span><span class="sxs-lookup"><span data-stu-id="2306c-128">Directly associated with variable's value</span></span>|<span data-ttu-id="2306c-129">通常在屬性的包含類別或模組之外，無法使用內部儲存體</span><span class="sxs-lookup"><span data-stu-id="2306c-129">Typically has internal storage not available outside the property's containing class or module</span></span><br /><br /> <span data-ttu-id="2306c-130">屬性的值不一定會以預存元素的形式存在<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2306c-130">Property's value might or might not exist as a stored element <sup>1</sup></span></span>|  
|<span data-ttu-id="2306c-131">可執行程式碼</span><span class="sxs-lookup"><span data-stu-id="2306c-131">Executable code</span></span>|<span data-ttu-id="2306c-132">無</span><span class="sxs-lookup"><span data-stu-id="2306c-132">None</span></span>|<span data-ttu-id="2306c-133">必須至少有一個程式</span><span class="sxs-lookup"><span data-stu-id="2306c-133">Must have at least one procedure</span></span>|  
|<span data-ttu-id="2306c-134">讀取和寫入存取權</span><span class="sxs-lookup"><span data-stu-id="2306c-134">Read and write access</span></span>|<span data-ttu-id="2306c-135">讀取/寫入或唯讀</span><span class="sxs-lookup"><span data-stu-id="2306c-135">Read/write or read-only</span></span>|<span data-ttu-id="2306c-136">讀取/寫入、唯讀或僅限寫入</span><span class="sxs-lookup"><span data-stu-id="2306c-136">Read/write, read-only, or write-only</span></span>|  
|<span data-ttu-id="2306c-137">自訂動作（除了接受或傳回值以外）</span><span class="sxs-lookup"><span data-stu-id="2306c-137">Custom actions (in addition to accepting or returning value)</span></span>|<span data-ttu-id="2306c-138">不可能</span><span class="sxs-lookup"><span data-stu-id="2306c-138">Not possible</span></span>|<span data-ttu-id="2306c-139">可以做為設定或抓取屬性值的一部分來執行</span><span class="sxs-lookup"><span data-stu-id="2306c-139">Can be performed as part of setting or retrieving property value</span></span>|  
  
 <span data-ttu-id="2306c-140"><sup>1</sup>與變數不同的是，屬性的值可能不會直接對應至單一的儲存專案。</span><span class="sxs-lookup"><span data-stu-id="2306c-140"><sup>1</sup> Unlike a variable, the value of a property might not correspond directly to a single item of storage.</span></span> <span data-ttu-id="2306c-141">儲存區可能會分割成方便或安全性的部分，或者值可能會以加密形式儲存。</span><span class="sxs-lookup"><span data-stu-id="2306c-141">The storage might be split into pieces for convenience or security, or the value might be stored in an encrypted form.</span></span> <span data-ttu-id="2306c-142">在這些情況下，程式 `Get` 會組合部分或解密儲存的值，而程式 `Set` 會加密新的值，或將它分割成構成儲存體。</span><span class="sxs-lookup"><span data-stu-id="2306c-142">In these cases the `Get` procedure would assemble the pieces or decrypt the stored value, and the `Set` procedure would encrypt the new value or split it into the constituent storage.</span></span> <span data-ttu-id="2306c-143">屬性值可能是暫時的，像是一天的時間，在這種情況下，程式 `Get` 會在每次存取屬性時即時計算它。</span><span class="sxs-lookup"><span data-stu-id="2306c-143">A property value might be ephemeral, like time of day, in which case the `Get` procedure would calculate it on the fly each time you access the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2306c-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2306c-144">See also</span></span>

- [<span data-ttu-id="2306c-145">屬性程序</span><span class="sxs-lookup"><span data-stu-id="2306c-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="2306c-146">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="2306c-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2306c-147">Property Statement</span><span class="sxs-lookup"><span data-stu-id="2306c-147">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="2306c-148">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="2306c-148">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="2306c-149">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="2306c-149">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="2306c-150">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="2306c-150">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="2306c-151">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="2306c-151">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="2306c-152">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="2306c-152">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="2306c-153">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="2306c-153">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="2306c-154">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="2306c-154">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
