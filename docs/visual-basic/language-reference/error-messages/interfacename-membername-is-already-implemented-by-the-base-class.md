---
title: 基底類別 '<baseclassname>' 已實作 '<interfacename>.<membername>'。 假設要重新實作 <type>
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 8137f6b1712b6a0752a991f5a3d598b5f958252c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162813"
---
# <a name="bc42015-interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a><span data-ttu-id="7751f-103">BC42015： ' \<interfacename> . \<membername> ' 已經由基類 ' ' 實作為 \<baseclassname> 。</span><span class="sxs-lookup"><span data-stu-id="7751f-103">BC42015: '\<interfacename>.\<membername>' is already implemented by the base class '\<baseclassname>'.</span></span> <span data-ttu-id="7751f-104">假設要重新實作 \<type></span><span class="sxs-lookup"><span data-stu-id="7751f-104">Re-implementation of \<type> assumed</span></span>

<span data-ttu-id="7751f-105">衍生類別中的屬性、程式或事件使用 `Implements` 子句來指定已在基類中執行的介面成員。</span><span class="sxs-lookup"><span data-stu-id="7751f-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>

 <span data-ttu-id="7751f-106">衍生類別可以重新實作透過其基底類別所實作的介面成員。</span><span class="sxs-lookup"><span data-stu-id="7751f-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="7751f-107">這與覆寫基底類別實作不同。</span><span class="sxs-lookup"><span data-stu-id="7751f-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="7751f-108">如需詳細資訊，請參閱 [Implements](../statements/implements-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="7751f-108">For more information, see [Implements](../statements/implements-clause.md).</span></span>

 <span data-ttu-id="7751f-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="7751f-109">By default, this message is a warning.</span></span> <span data-ttu-id="7751f-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="7751f-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="7751f-111">**錯誤識別碼：** BC42015</span><span class="sxs-lookup"><span data-stu-id="7751f-111">**Error ID:** BC42015</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7751f-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7751f-112">To correct this error</span></span>

- <span data-ttu-id="7751f-113">如果您要重新實作介面成員，則不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="7751f-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="7751f-114">除非您使用 `MyBase` 關鍵字來存取基類執行，否則衍生類別中的程式碼會存取根據成員。</span><span class="sxs-lookup"><span data-stu-id="7751f-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>

- <span data-ttu-id="7751f-115">如果您不要重新實作介面成員，請從屬性、程序或事件宣告中移除 `Implements` 子句。</span><span class="sxs-lookup"><span data-stu-id="7751f-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="7751f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7751f-116">See also</span></span>

- [<span data-ttu-id="7751f-117">介面</span><span class="sxs-lookup"><span data-stu-id="7751f-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
