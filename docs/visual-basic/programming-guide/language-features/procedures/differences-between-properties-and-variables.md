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
ms.openlocfilehash: 95bafcaca98e1a0fbdd62a550291c8ece932c1ba
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075027"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a><span data-ttu-id="c3ea7-102">Visual Basic 中屬性和變數的差別</span><span class="sxs-lookup"><span data-stu-id="c3ea7-102">Differences Between Properties and Variables in Visual Basic</span></span>

<span data-ttu-id="c3ea7-103">變數和屬性都代表您可以存取的值。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-103">Variables and properties both represent values that you can access.</span></span> <span data-ttu-id="c3ea7-104">不過，儲存體和執行之間有一些差異。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-104">However, there are differences in storage and implementation.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="c3ea7-105">變數</span><span class="sxs-lookup"><span data-stu-id="c3ea7-105">Variables</span></span>  

 <span data-ttu-id="c3ea7-106">*變數*會直接對應到記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-106">A *variable* corresponds directly to a memory location.</span></span> <span data-ttu-id="c3ea7-107">您可以使用單一宣告語句來定義變數。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-107">You define a variable with a single declaration statement.</span></span> <span data-ttu-id="c3ea7-108">變數可以是在程式內定義的 *區域變數*，而且只能在該程式中使用，也可以是在模組、類別或結構中定義的 *成員變數*，而不是在任何程式內。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-108">A variable can be a *local variable*, defined inside a procedure and available only within that procedure, or it can be a *member variable*, defined in a module, class, or structure but not inside any procedure.</span></span> <span data-ttu-id="c3ea7-109">成員變數也稱為 *欄位*。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-109">A member variable is also called a *field*.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c3ea7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c3ea7-110">Properties</span></span>  

 <span data-ttu-id="c3ea7-111">*屬性*是在模組、類別或結構上定義的資料元素。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-111">A *property* is a data element defined on a module, class, or structure.</span></span> <span data-ttu-id="c3ea7-112">您可以使用和語句之間的程式碼區塊來定義屬性 `Property` `End Property` 。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-112">You define a property with a code block between the `Property` and `End Property` statements.</span></span> <span data-ttu-id="c3ea7-113">程式碼區塊包含程式 `Get` 、程式 `Set` 或兩者。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-113">The code block contains a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="c3ea7-114">這些程式稱為 *屬性程式* 或 *屬性存取*子。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-114">These procedures are called *property procedures* or *property accessors*.</span></span> <span data-ttu-id="c3ea7-115">除了抓取或儲存屬性的值之外，也可以執行自訂動作，例如更新存取計數器。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-115">In addition to retrieving or storing the property's value, they can also perform custom actions, such as updating an access counter.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="c3ea7-116">差異</span><span class="sxs-lookup"><span data-stu-id="c3ea7-116">Differences</span></span>  

 <span data-ttu-id="c3ea7-117">下表顯示變數和屬性之間的一些重要差異。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-117">The following table shows some important differences between variables and properties.</span></span>  
  
|<span data-ttu-id="c3ea7-118">差異點</span><span class="sxs-lookup"><span data-stu-id="c3ea7-118">Point of difference</span></span>|<span data-ttu-id="c3ea7-119">變數</span><span class="sxs-lookup"><span data-stu-id="c3ea7-119">Variable</span></span>|<span data-ttu-id="c3ea7-120">屬性</span><span class="sxs-lookup"><span data-stu-id="c3ea7-120">Property</span></span>|  
|-------------------------|--------------|--------------|  
|<span data-ttu-id="c3ea7-121">宣告</span><span class="sxs-lookup"><span data-stu-id="c3ea7-121">Declaration</span></span>|<span data-ttu-id="c3ea7-122">Single 宣告語句</span><span class="sxs-lookup"><span data-stu-id="c3ea7-122">Single declaration statement</span></span>|<span data-ttu-id="c3ea7-123">程式碼區塊中的語句系列</span><span class="sxs-lookup"><span data-stu-id="c3ea7-123">Series of statements in a code block</span></span>|  
|<span data-ttu-id="c3ea7-124">實作</span><span class="sxs-lookup"><span data-stu-id="c3ea7-124">Implementation</span></span>|<span data-ttu-id="c3ea7-125">單一儲存體位置</span><span class="sxs-lookup"><span data-stu-id="c3ea7-125">Single storage location</span></span>|<span data-ttu-id="c3ea7-126">可執行程式碼 (屬性程式) </span><span class="sxs-lookup"><span data-stu-id="c3ea7-126">Executable code (property procedures)</span></span>|  
|<span data-ttu-id="c3ea7-127">儲存體</span><span class="sxs-lookup"><span data-stu-id="c3ea7-127">Storage</span></span>|<span data-ttu-id="c3ea7-128">直接關聯至變數的值</span><span class="sxs-lookup"><span data-stu-id="c3ea7-128">Directly associated with variable's value</span></span>|<span data-ttu-id="c3ea7-129">通常無法在屬性的包含類別或模組之外使用內部儲存體</span><span class="sxs-lookup"><span data-stu-id="c3ea7-129">Typically has internal storage not available outside the property's containing class or module</span></span><br /><br /> <span data-ttu-id="c3ea7-130">屬性的值不一定會以預存元素<sup>1</sup>的形式存在</span><span class="sxs-lookup"><span data-stu-id="c3ea7-130">Property's value might or might not exist as a stored element <sup>1</sup></span></span>|  
|<span data-ttu-id="c3ea7-131">可執行程式碼</span><span class="sxs-lookup"><span data-stu-id="c3ea7-131">Executable code</span></span>|<span data-ttu-id="c3ea7-132">無</span><span class="sxs-lookup"><span data-stu-id="c3ea7-132">None</span></span>|<span data-ttu-id="c3ea7-133">至少必須有一個程式</span><span class="sxs-lookup"><span data-stu-id="c3ea7-133">Must have at least one procedure</span></span>|  
|<span data-ttu-id="c3ea7-134">讀取和寫入存取權</span><span class="sxs-lookup"><span data-stu-id="c3ea7-134">Read and write access</span></span>|<span data-ttu-id="c3ea7-135">讀取/寫入或唯讀</span><span class="sxs-lookup"><span data-stu-id="c3ea7-135">Read/write or read-only</span></span>|<span data-ttu-id="c3ea7-136">讀/寫、唯讀或僅限寫入</span><span class="sxs-lookup"><span data-stu-id="c3ea7-136">Read/write, read-only, or write-only</span></span>|  
|<span data-ttu-id="c3ea7-137">除了接受或傳回值之外，還 (自訂動作) </span><span class="sxs-lookup"><span data-stu-id="c3ea7-137">Custom actions (in addition to accepting or returning value)</span></span>|<span data-ttu-id="c3ea7-138">不可能</span><span class="sxs-lookup"><span data-stu-id="c3ea7-138">Not possible</span></span>|<span data-ttu-id="c3ea7-139">可作為設定或抓取屬性值的一部分來執行</span><span class="sxs-lookup"><span data-stu-id="c3ea7-139">Can be performed as part of setting or retrieving property value</span></span>|  
  
 <span data-ttu-id="c3ea7-140"><sup>1</sup> 與變數不同的是，屬性的值可能不會直接對應到儲存區的單一專案。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-140"><sup>1</sup> Unlike a variable, the value of a property might not correspond directly to a single item of storage.</span></span> <span data-ttu-id="c3ea7-141">儲存體可能會分割成方便或安全性的部分，或者值可能會以加密形式儲存。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-141">The storage might be split into pieces for convenience or security, or the value might be stored in an encrypted form.</span></span> <span data-ttu-id="c3ea7-142">在這些情況下，程式 `Get` 會組合片段或解密儲存的值，而此程式 `Set` 會加密新的值，或將其分割成構成的儲存體。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-142">In these cases the `Get` procedure would assemble the pieces or decrypt the stored value, and the `Set` procedure would encrypt the new value or split it into the constituent storage.</span></span> <span data-ttu-id="c3ea7-143">屬性值可能是暫時的，就像是一天中的時間，在這種情況下，程式 `Get` 會在您每次存取屬性時將它即時計算。</span><span class="sxs-lookup"><span data-stu-id="c3ea7-143">A property value might be ephemeral, like time of day, in which case the `Get` procedure would calculate it on the fly each time you access the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ea7-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3ea7-144">See also</span></span>

- [<span data-ttu-id="c3ea7-145">屬性程序</span><span class="sxs-lookup"><span data-stu-id="c3ea7-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="c3ea7-146">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="c3ea7-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c3ea7-147">Property Statement</span><span class="sxs-lookup"><span data-stu-id="c3ea7-147">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="c3ea7-148">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="c3ea7-148">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="c3ea7-149">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="c3ea7-149">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="c3ea7-150">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="c3ea7-150">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="c3ea7-151">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="c3ea7-151">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="c3ea7-152">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="c3ea7-152">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="c3ea7-153">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="c3ea7-153">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="c3ea7-154">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="c3ea7-154">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
