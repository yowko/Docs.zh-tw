---
title: "將 .NET Framework 型別轉換成字串"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6ca134e13593fdacd759b0000e0e159f76ea067f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="be6b6-102">將 .NET Framework 型別轉換成字串</span><span class="sxs-lookup"><span data-stu-id="be6b6-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="be6b6-103">若要將 .NET Framework 型別轉換成字串，請使用 **ToString** 方法。</span><span class="sxs-lookup"><span data-stu-id="be6b6-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="be6b6-104">**ToString** 方法會傳回所傳入之型別的字串表示。</span><span class="sxs-lookup"><span data-stu-id="be6b6-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="be6b6-105">下表將列出 .NET Framework 型別，其所傳回的字串格式會對應至 XML 結構描述 (XSD) 規格。</span><span class="sxs-lookup"><span data-stu-id="be6b6-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="be6b6-106">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="be6b6-106">.NET Framework type</span></span>|<span data-ttu-id="be6b6-107">傳回的字串型別</span><span class="sxs-lookup"><span data-stu-id="be6b6-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="be6b6-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="be6b6-108">Boolean</span></span>|<span data-ttu-id="be6b6-109">"true"、"false"</span><span class="sxs-lookup"><span data-stu-id="be6b6-109">"true", "false"</span></span>|  
|<span data-ttu-id="be6b6-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="be6b6-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="be6b6-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="be6b6-111">"INF"</span></span>|  
|<span data-ttu-id="be6b6-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="be6b6-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="be6b6-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="be6b6-113">"-INF"</span></span>|  
|<span data-ttu-id="be6b6-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="be6b6-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="be6b6-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="be6b6-115">"INF"</span></span>|  
|<span data-ttu-id="be6b6-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="be6b6-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="be6b6-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="be6b6-117">"-INF"</span></span>|  
|<span data-ttu-id="be6b6-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="be6b6-118">DateTime</span></span>|<span data-ttu-id="be6b6-119">格式為 yyyy-MM-ddTHH:mm:sszzzzzz 及其子集。</span><span class="sxs-lookup"><span data-stu-id="be6b6-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="be6b6-120">Timespan</span><span class="sxs-lookup"><span data-stu-id="be6b6-120">Timespan</span></span>|<span data-ttu-id="be6b6-121">格式為 PnYnMnTnHnMnS，例如 `P2Y10M15DT10H30M20S` 代表期間為 2 年 10 個月 15 天 10 小時 30 分鐘 20 秒。</span><span class="sxs-lookup"><span data-stu-id="be6b6-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be6b6-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="be6b6-122">See Also</span></span>  
 [<span data-ttu-id="be6b6-123">XML 資料類型轉換</span><span class="sxs-lookup"><span data-stu-id="be6b6-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [<span data-ttu-id="be6b6-124">將字串轉換成 .NET Framework 資料類型</span><span class="sxs-lookup"><span data-stu-id="be6b6-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
