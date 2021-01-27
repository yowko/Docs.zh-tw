---
title: '如何撰寫複製函式-c # 程式設計手冊'
description: '瞭解如何在 c # 中撰寫使用類別實例的複製函式，並傳回具有輸入值的新實例。'
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: db26b26ebcc51b57fdbe58ddaf92e5019cb69659
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899382"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="109f0-103">如何撰寫複製函式 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="109f0-103">How to write a copy constructor (C# Programming Guide)</span></span>

<span data-ttu-id="109f0-104">C# 未提供物件的複製建構函式，但您可以自行撰寫一個。</span><span class="sxs-lookup"><span data-stu-id="109f0-104">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="109f0-105">範例</span><span class="sxs-lookup"><span data-stu-id="109f0-105">Example</span></span>  

 <span data-ttu-id="109f0-106">在下列範例中，`Person`[類別](../../language-reference/keywords/class.md)定義接受 `Person` 執行個體作為其引數的複製建構函式。</span><span class="sxs-lookup"><span data-stu-id="109f0-106">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="109f0-107">引數的屬性值會指派給新 `Person` 執行個體的屬性。</span><span class="sxs-lookup"><span data-stu-id="109f0-107">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="109f0-108">這個程式碼包含替代的複製建構函式，可將您想要複製之執行個體的 `Name` 和 `Age` 屬性傳送給類別的執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="109f0-108">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[CopyConstructor](snippets/how-to-write-a-copy-constructor/Program.cs)]
  
## <a name="see-also"></a><span data-ttu-id="109f0-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="109f0-109">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="109f0-110">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="109f0-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="109f0-111">類別和結構</span><span class="sxs-lookup"><span data-stu-id="109f0-111">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="109f0-112">建構函式</span><span class="sxs-lookup"><span data-stu-id="109f0-112">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="109f0-113">完成項</span><span class="sxs-lookup"><span data-stu-id="109f0-113">Finalizers</span></span>](./destructors.md)
