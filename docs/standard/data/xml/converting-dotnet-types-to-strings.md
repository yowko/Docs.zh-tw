---
title: 將 .NET 類型轉換成字串
ms.date: 03/30/2017
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: 9744224b4346b865a112b0eb6957f12553e1ec5f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830983"
---
# <a name="convert-net-types-to-strings"></a><span data-ttu-id="1c412-102">將 .NET 類型轉換成字串</span><span class="sxs-lookup"><span data-stu-id="1c412-102">Convert .NET types to strings</span></span>

<span data-ttu-id="1c412-103">如果您想要將 .NET 型別轉換成字串，請使用 **ToString** 方法。</span><span class="sxs-lookup"><span data-stu-id="1c412-103">If you want to convert a .NET type to a string, use the **ToString** method.</span></span> <span data-ttu-id="1c412-104">**ToString** 方法會傳回所傳入之型別的字串表示。</span><span class="sxs-lookup"><span data-stu-id="1c412-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="1c412-105">下表列出的 .NET 型別會以對應至 XML 架構 (XSD) 規格的格式傳回字串。</span><span class="sxs-lookup"><span data-stu-id="1c412-105">The following table lists the .NET types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="1c412-106">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="1c412-106">.NET type</span></span>|<span data-ttu-id="1c412-107">傳回的字串型別</span><span class="sxs-lookup"><span data-stu-id="1c412-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="1c412-108">布林值</span><span class="sxs-lookup"><span data-stu-id="1c412-108">Boolean</span></span>|<span data-ttu-id="1c412-109">"true"、"false"</span><span class="sxs-lookup"><span data-stu-id="1c412-109">"true", "false"</span></span>|  
|<span data-ttu-id="1c412-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="1c412-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="1c412-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="1c412-111">"INF"</span></span>|  
|<span data-ttu-id="1c412-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="1c412-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="1c412-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="1c412-113">"-INF"</span></span>|  
|<span data-ttu-id="1c412-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="1c412-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="1c412-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="1c412-115">"INF"</span></span>|  
|<span data-ttu-id="1c412-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="1c412-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="1c412-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="1c412-117">"-INF"</span></span>|  
|<span data-ttu-id="1c412-118">Datetime</span><span class="sxs-lookup"><span data-stu-id="1c412-118">DateTime</span></span>|<span data-ttu-id="1c412-119">格式為 yyyy-MM-ddTHH:mm:sszzzzzz 及其子集。</span><span class="sxs-lookup"><span data-stu-id="1c412-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="1c412-120">Timespan</span><span class="sxs-lookup"><span data-stu-id="1c412-120">Timespan</span></span>|<span data-ttu-id="1c412-121">格式為 PnYnMnTnHnMnS，例如 `P2Y10M15DT10H30M20S` 代表期間為 2 年 10 個月 15 天 10 小時 30 分鐘 20 秒。</span><span class="sxs-lookup"><span data-stu-id="1c412-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c412-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="1c412-122">See also</span></span>

- [<span data-ttu-id="1c412-123">XML 資料型別轉換</span><span class="sxs-lookup"><span data-stu-id="1c412-123">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="1c412-124">將字串轉換成 .NET 資料類型</span><span class="sxs-lookup"><span data-stu-id="1c412-124">Converting Strings to .NET Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
