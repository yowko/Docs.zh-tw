---
title: 無法參考至 '<name>'，因為它是類別 '<name>' 的實值類型欄位 '<classname>' 的成員，它把 'System.MarshalByRefObject' 當做基底類別
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: 78b0a3131b6e77ed257f200523ecebd4dfce3691
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316540"
---
# <a name="cannot-refer-to-name-because-it-is-a-member-of-the-value-typed-field-name-of-class-classname-which-has-systemmarshalbyrefobject-as-a-base-class"></a><span data-ttu-id="5cd98-102">無法參考 '\<名稱 >' 因為它是實值類型欄位的成員'\<名稱 >' 的類別\<類別名稱 >' 'system.marshalbyrefobject' 當做基底類別</span><span class="sxs-lookup"><span data-stu-id="5cd98-102">Cannot refer to '\<name>' because it is a member of the value-typed field '\<name>' of class '\<classname>' which has 'System.MarshalByRefObject' as a base class</span></span>
<span data-ttu-id="5cd98-103">`System.MarshalByRefObject`類別可讓您跨應用程式定義域界限支援遠端物件的存取權的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cd98-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="5cd98-104">類型必須繼承自`MarshalByRejectObject`類別，在跨應用程式定義域界限使用的型別。</span><span class="sxs-lookup"><span data-stu-id="5cd98-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="5cd98-105">因為物件的成員不是他們所建立的應用程式定義域外使用，必須不會複製物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="5cd98-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="5cd98-106">**錯誤 ID:** BC30310</span><span class="sxs-lookup"><span data-stu-id="5cd98-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5cd98-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5cd98-107">To correct this error</span></span>  
  
1. <span data-ttu-id="5cd98-108">請檢查以確定所參考的成員都是有效的參考。</span><span class="sxs-lookup"><span data-stu-id="5cd98-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2. <span data-ttu-id="5cd98-109">明確限定的成員`Me`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5cd98-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd98-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cd98-110">See also</span></span>

- <xref:System.MarshalByRefObject>
- [<span data-ttu-id="5cd98-111">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="5cd98-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
