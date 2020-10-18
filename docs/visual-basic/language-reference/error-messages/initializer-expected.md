---
title: 必須是初始設定式
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: cbe77bab3e4f8bf2094c70c1c16d95ee897c729e
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163008"
---
# <a name="bc30996-initializer-expected"></a><span data-ttu-id="0aadb-102">BC30996：需要初始化運算式</span><span class="sxs-lookup"><span data-stu-id="0aadb-102">BC30996: Initializer expected</span></span>

<span data-ttu-id="0aadb-103">您已嘗試使用物件初始化運算式宣告類別的實例，其中的初始化清單是空的，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0aadb-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>

 `' Not valid.`

 `' Dim aStudent As New Student With {}`

 <span data-ttu-id="0aadb-104">必須在初始化運算式清單中初始化至少一個欄位或屬性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0aadb-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>

 `Dim aStudent As New Student With {.year = "Senior"}`

 <span data-ttu-id="0aadb-105">**錯誤識別碼：** BC30996</span><span class="sxs-lookup"><span data-stu-id="0aadb-105">**Error ID:** BC30996</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0aadb-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="0aadb-106">To correct this error</span></span>

- <span data-ttu-id="0aadb-107">在初始化運算式中至少初始化一個欄位或屬性，或不要使用物件初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="0aadb-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>

## <a name="see-also"></a><span data-ttu-id="0aadb-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0aadb-108">See also</span></span>

- [<span data-ttu-id="0aadb-109">物件初始設定式：具名和匿名型別</span><span class="sxs-lookup"><span data-stu-id="0aadb-109">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="0aadb-110">如何：使用物件初始設定式宣告物件</span><span class="sxs-lookup"><span data-stu-id="0aadb-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
