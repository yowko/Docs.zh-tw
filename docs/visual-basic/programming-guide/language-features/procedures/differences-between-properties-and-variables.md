---
title: "Visual Basic 中屬性和變數的差別"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cb30972e2b49a7005749f57c0223b9fa493cde52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a><span data-ttu-id="3dacf-102">Visual Basic 中屬性和變數的差別</span><span class="sxs-lookup"><span data-stu-id="3dacf-102">Differences Between Properties and Variables in Visual Basic</span></span>
<span data-ttu-id="3dacf-103">變數和屬性都代表您可以存取的值。</span><span class="sxs-lookup"><span data-stu-id="3dacf-103">Variables and properties both represent values that you can access.</span></span> <span data-ttu-id="3dacf-104">不過，有儲存體與實作中的差異。</span><span class="sxs-lookup"><span data-stu-id="3dacf-104">However, there are differences in storage and implementation.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="3dacf-105">變數</span><span class="sxs-lookup"><span data-stu-id="3dacf-105">Variables</span></span>  
 <span data-ttu-id="3dacf-106">A*變數*直接對應到記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="3dacf-106">A *variable* corresponds directly to a memory location.</span></span> <span data-ttu-id="3dacf-107">您定義的單一宣告陳述式的變數。</span><span class="sxs-lookup"><span data-stu-id="3dacf-107">You define a variable with a single declaration statement.</span></span> <span data-ttu-id="3dacf-108">變數可以是*區域變數*、 定義程序內，只能在該程序，或它可以是*成員變數*、 模組、 類別或結構中，但不是能在任何定義程序。</span><span class="sxs-lookup"><span data-stu-id="3dacf-108">A variable can be a *local variable*, defined inside a procedure and available only within that procedure, or it can be a *member variable*, defined in a module, class, or structure but not inside any procedure.</span></span> <span data-ttu-id="3dacf-109">成員變數，也會呼叫*欄位*。</span><span class="sxs-lookup"><span data-stu-id="3dacf-109">A member variable is also called a *field*.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3dacf-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3dacf-110">Properties</span></span>  
 <span data-ttu-id="3dacf-111">A*屬性*是模組、 類別或結構上定義的資料元素。</span><span class="sxs-lookup"><span data-stu-id="3dacf-111">A *property* is a data element defined on a module, class, or structure.</span></span> <span data-ttu-id="3dacf-112">定義屬性之間的程式碼區塊與`Property`和`End Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3dacf-112">You define a property with a code block between the `Property` and `End Property` statements.</span></span> <span data-ttu-id="3dacf-113">程式碼區塊包含`Get`程序，`Set`程序，或兩者。</span><span class="sxs-lookup"><span data-stu-id="3dacf-113">The code block contains a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="3dacf-114">這些程序稱為*屬性程序*或*屬性存取子*。</span><span class="sxs-lookup"><span data-stu-id="3dacf-114">These procedures are called *property procedures* or *property accessors*.</span></span> <span data-ttu-id="3dacf-115">除了擷取，或儲存屬性的值，他們也可以執行自訂動作，例如更新存取計數器。</span><span class="sxs-lookup"><span data-stu-id="3dacf-115">In addition to retrieving or storing the property's value, they can also perform custom actions, such as updating an access counter.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="3dacf-116">差異</span><span class="sxs-lookup"><span data-stu-id="3dacf-116">Differences</span></span>  
 <span data-ttu-id="3dacf-117">下表顯示變數和屬性之間的一些重要差異。</span><span class="sxs-lookup"><span data-stu-id="3dacf-117">The following table shows some important differences between variables and properties.</span></span>  
  
|<span data-ttu-id="3dacf-118">差異點</span><span class="sxs-lookup"><span data-stu-id="3dacf-118">Point of difference</span></span>|<span data-ttu-id="3dacf-119">變數</span><span class="sxs-lookup"><span data-stu-id="3dacf-119">Variable</span></span>|<span data-ttu-id="3dacf-120">屬性</span><span class="sxs-lookup"><span data-stu-id="3dacf-120">Property</span></span>|  
|-------------------------|--------------|--------------|  
|<span data-ttu-id="3dacf-121">宣告</span><span class="sxs-lookup"><span data-stu-id="3dacf-121">Declaration</span></span>|<span data-ttu-id="3dacf-122">單一宣告陳述式</span><span class="sxs-lookup"><span data-stu-id="3dacf-122">Single declaration statement</span></span>|<span data-ttu-id="3dacf-123">系列的程式碼區塊中的陳述式</span><span class="sxs-lookup"><span data-stu-id="3dacf-123">Series of statements in a code block</span></span>|  
|<span data-ttu-id="3dacf-124">實作</span><span class="sxs-lookup"><span data-stu-id="3dacf-124">Implementation</span></span>|<span data-ttu-id="3dacf-125">單一儲存體位置</span><span class="sxs-lookup"><span data-stu-id="3dacf-125">Single storage location</span></span>|<span data-ttu-id="3dacf-126">可執行程式碼 （屬性程序）</span><span class="sxs-lookup"><span data-stu-id="3dacf-126">Executable code (property procedures)</span></span>|  
|<span data-ttu-id="3dacf-127">儲存區</span><span class="sxs-lookup"><span data-stu-id="3dacf-127">Storage</span></span>|<span data-ttu-id="3dacf-128">直接相關聯的變數值</span><span class="sxs-lookup"><span data-stu-id="3dacf-128">Directly associated with variable's value</span></span>|<span data-ttu-id="3dacf-129">通常會有包含屬性的類別或模組外部無法使用的內部儲存體</span><span class="sxs-lookup"><span data-stu-id="3dacf-129">Typically has internal storage not available outside the property's containing class or module</span></span><br /><br /> <span data-ttu-id="3dacf-130">屬性的值可能會或可能不存在的預存的項目為<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3dacf-130">Property's value might or might not exist as a stored element <sup>1</sup></span></span>|  
|<span data-ttu-id="3dacf-131">可執行程式碼</span><span class="sxs-lookup"><span data-stu-id="3dacf-131">Executable code</span></span>|<span data-ttu-id="3dacf-132">無</span><span class="sxs-lookup"><span data-stu-id="3dacf-132">None</span></span>|<span data-ttu-id="3dacf-133">必須至少一個程序</span><span class="sxs-lookup"><span data-stu-id="3dacf-133">Must have at least one procedure</span></span>|  
|<span data-ttu-id="3dacf-134">讀取和寫入存取</span><span class="sxs-lookup"><span data-stu-id="3dacf-134">Read and write access</span></span>|<span data-ttu-id="3dacf-135">讀/寫或唯讀</span><span class="sxs-lookup"><span data-stu-id="3dacf-135">Read/write or read-only</span></span>|<span data-ttu-id="3dacf-136">讀取/寫入，唯讀或唯寫</span><span class="sxs-lookup"><span data-stu-id="3dacf-136">Read/write, read-only, or write-only</span></span>|  
|<span data-ttu-id="3dacf-137">自訂動作 （除了接受或傳回值）</span><span class="sxs-lookup"><span data-stu-id="3dacf-137">Custom actions (in addition to accepting or returning value)</span></span>|<span data-ttu-id="3dacf-138">不可能</span><span class="sxs-lookup"><span data-stu-id="3dacf-138">Not possible</span></span>|<span data-ttu-id="3dacf-139">可以執行設定或擷取屬性值的一部分</span><span class="sxs-lookup"><span data-stu-id="3dacf-139">Can be performed as part of setting or retrieving property value</span></span>|  
  
 <span data-ttu-id="3dacf-140"><sup>1</sup>不同變數中，於屬性的值可能不直接對應至儲存體的單一項目。</span><span class="sxs-lookup"><span data-stu-id="3dacf-140"><sup>1</sup> Unlike a variable, the value of a property might not correspond directly to a single item of storage.</span></span> <span data-ttu-id="3dacf-141">儲存體可能會分成片段方便或安全性，或值可能會以加密格式儲存。</span><span class="sxs-lookup"><span data-stu-id="3dacf-141">The storage might be split into pieces for convenience or security, or the value might be stored in an encrypted form.</span></span> <span data-ttu-id="3dacf-142">在這些情況下`Get`程序會組合在一起，或解密儲存的值，而`Set`程序會加密新的值，或將它分割為組成儲存體。</span><span class="sxs-lookup"><span data-stu-id="3dacf-142">In these cases the `Get` procedure would assemble the pieces or decrypt the stored value, and the `Set` procedure would encrypt the new value or split it into the constituent storage.</span></span> <span data-ttu-id="3dacf-143">屬性值在此情況下可能是暫時的例如每日`Get`程序會計算會即時每次存取屬性。</span><span class="sxs-lookup"><span data-stu-id="3dacf-143">A property value might be ephemeral, like time of day, in which case the `Get` procedure would calculate it on the fly each time you access the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dacf-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3dacf-144">See Also</span></span>  
 [<span data-ttu-id="3dacf-145">屬性程序</span><span class="sxs-lookup"><span data-stu-id="3dacf-145">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="3dacf-146">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="3dacf-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="3dacf-147">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="3dacf-147">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="3dacf-148">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="3dacf-148">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="3dacf-149">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="3dacf-149">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="3dacf-150">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="3dacf-150">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="3dacf-151">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="3dacf-151">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="3dacf-152">如何： 宣告及呼叫在 Visual Basic 中的預設屬性</span><span class="sxs-lookup"><span data-stu-id="3dacf-152">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="3dacf-153">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="3dacf-153">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="3dacf-154">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="3dacf-154">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
