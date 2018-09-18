---
title: 設定狀態資料的安全性
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c821177ca897e617885425217ac0b6659b5ea6e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003447"
---
# <a name="securing-state-data"></a><span data-ttu-id="8ca9f-102">設定狀態資料的安全性</span><span class="sxs-lookup"><span data-stu-id="8ca9f-102">Securing State Data</span></span>
<span data-ttu-id="8ca9f-103">處理機密資料或執行任何種類安全性決策的應用程式需要保持該資料在自己的控制之下，而且不能允許其他潛在惡意程式碼直接存取資料。</span><span class="sxs-lookup"><span data-stu-id="8ca9f-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="8ca9f-104">保護記憶體中資料的最佳方式是將資料宣告為私用或內部 (具有限制為相同組件的範圍) 變數。</span><span class="sxs-lookup"><span data-stu-id="8ca9f-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="8ca9f-105">不過，即使此資料受限於存取權，您應該要注意︰</span><span class="sxs-lookup"><span data-stu-id="8ca9f-105">However, even this data is subject to access you should be aware of:</span></span>  
  
-   <span data-ttu-id="8ca9f-106">使用反映機制，可以參考您物件的高度信任程式碼可以取得和設定私用成員。</span><span class="sxs-lookup"><span data-stu-id="8ca9f-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
-   <span data-ttu-id="8ca9f-107">使用序列化，如果高度信任程式碼可以使用物件的序列化格式存取對應的資料，則高度信任程式碼可以有效地取得和設定私用成員。</span><span class="sxs-lookup"><span data-stu-id="8ca9f-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
-   <span data-ttu-id="8ca9f-108">在偵錯時，可以讀取此資料。</span><span class="sxs-lookup"><span data-stu-id="8ca9f-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="8ca9f-109">請確定沒有任何您自己的方法或屬性會在無意中公開這些值。</span><span class="sxs-lookup"><span data-stu-id="8ca9f-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca9f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ca9f-110">See also</span></span>

- [<span data-ttu-id="8ca9f-111">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="8ca9f-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
