---
title: " (程式碼分析) 的全球化規則"
description: 瞭解程式碼分析規則的全球化規則
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- rules, globalization
- globalization rules
- globalization [Visual Studio], rules
- managed code analysis rules, globalization rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 83ecc52c5e20e074c6c1aed68204a574494f42d5
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "96586148"
---
# <a name="globalization-rules"></a><span data-ttu-id="df776-103">全球化規則</span><span class="sxs-lookup"><span data-stu-id="df776-103">Globalization rules</span></span>

<span data-ttu-id="df776-104">全球化規則支援可供世界用的程式庫和應用程式。</span><span class="sxs-lookup"><span data-stu-id="df776-104">Globalization rules support world-ready libraries and applications.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="df776-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="df776-105">In this section</span></span>

|<span data-ttu-id="df776-106">規則</span><span class="sxs-lookup"><span data-stu-id="df776-106">Rule</span></span>|<span data-ttu-id="df776-107">描述</span><span class="sxs-lookup"><span data-stu-id="df776-107">Description</span></span>|
|----------|-----------------|
|[<span data-ttu-id="df776-108">CA1303:不要將常值當作已當地語系化的參數傳遞</span><span class="sxs-lookup"><span data-stu-id="df776-108">CA1303: Do not pass literals as localized parameters</span></span>](ca1303.md)|<span data-ttu-id="df776-109">外部可見的方法會將字串常值做為參數傳遞至 .NET 的函式或方法，且該字串應可當地語系化。</span><span class="sxs-lookup"><span data-stu-id="df776-109">An externally visible method passes a string literal as a parameter to a .NET constructor or method, and that string should be localizable.</span></span>|
|[<span data-ttu-id="df776-110">CA1304:必須指定 CultureInfo</span><span class="sxs-lookup"><span data-stu-id="df776-110">CA1304: Specify CultureInfo</span></span>](ca1304.md)|<span data-ttu-id="df776-111">方法或建構函式會呼叫具有接受 System.Globalization.CultureInfo 參數之多載的成員，且方法或建構函式未呼叫採用 CultureInfo 參數的多載。</span><span class="sxs-lookup"><span data-stu-id="df776-111">A method or constructor calls a member that has an overload that accepts a System.Globalization.CultureInfo parameter, and the method or constructor does not call the overload that takes the CultureInfo parameter.</span></span> <span data-ttu-id="df776-112">未提供 CultureInfo 或 System.IFormatProvider 物件時，多載成員所提供的預設值可能不會有您希望在所有地區設定中都有的效果。</span><span class="sxs-lookup"><span data-stu-id="df776-112">When a CultureInfo or System.IFormatProvider object is not supplied, the default value that is supplied by the overloaded member might not have the effect that you want in all locales.</span></span>|
|[<span data-ttu-id="df776-113">CA1305:必須指定 IFormatProvider</span><span class="sxs-lookup"><span data-stu-id="df776-113">CA1305: Specify IFormatProvider</span></span>](ca1305.md)|<span data-ttu-id="df776-114">方法或建構函式所呼叫的一個或多個成員具有可接受 System.IFormatProvider 參數的多載，但該方法或建構函式並未呼叫可接受 IFormatProvider 參數的多載。</span><span class="sxs-lookup"><span data-stu-id="df776-114">A method or constructor calls one or more members that have overloads that accept a System.IFormatProvider parameter, and the method or constructor does not call the overload that takes the IFormatProvider parameter.</span></span> <span data-ttu-id="df776-115">未提供 System.Globalization.CultureInfo 或 IFormatProvider 物件時，多載成員所提供的預設值可能不會有您希望在所有地區設定中都有的效果。</span><span class="sxs-lookup"><span data-stu-id="df776-115">When a System.Globalization.CultureInfo or IFormatProvider object is not supplied, the default value that is supplied by the overloaded member might not have the effect that you want in all locales.</span></span>|
|[<span data-ttu-id="df776-116">CA1307:指定 StringComparison 以提升明確性</span><span class="sxs-lookup"><span data-stu-id="df776-116">CA1307: Specify StringComparison for clarity</span></span>](ca1307.md)|<span data-ttu-id="df776-117">字串比較作業會使用未設定 StringComparison 參數的方法多載。</span><span class="sxs-lookup"><span data-stu-id="df776-117">A string comparison operation uses a method overload that does not set a StringComparison parameter.</span></span>|
|[<span data-ttu-id="df776-118">CA1308:必須將字串標準化為大寫字母</span><span class="sxs-lookup"><span data-stu-id="df776-118">CA1308: Normalize strings to uppercase</span></span>](ca1308.md)|<span data-ttu-id="df776-119">字串應該標準化為大寫字母。</span><span class="sxs-lookup"><span data-stu-id="df776-119">Strings should be normalized to uppercase.</span></span> <span data-ttu-id="df776-120">當一小組的字元轉換成小寫字母時，它們無法構成來回行程。</span><span class="sxs-lookup"><span data-stu-id="df776-120">A small group of characters cannot make a round trip when they are converted to lowercase.</span></span>|
|[<span data-ttu-id="df776-121">CA1309:使用循序的 StringComparison</span><span class="sxs-lookup"><span data-stu-id="df776-121">CA1309: Use ordinal StringComparison</span></span>](ca1309.md)|<span data-ttu-id="df776-122">非語言的字串比較作業未將 StringComparison 參數設定為 Ordinal 或 OrdinalIgnoreCase。</span><span class="sxs-lookup"><span data-stu-id="df776-122">A string comparison operation that is nonlinguistic does not set the StringComparison parameter to either Ordinal or OrdinalIgnoreCase.</span></span> <span data-ttu-id="df776-123">藉由明確地將參數設定為 StringComparison.Ordinal 或 StringComparison.OrdinalIgnoreCase，您的程式碼通常可以提升速度、更為正確，也更加可靠。</span><span class="sxs-lookup"><span data-stu-id="df776-123">By explicitly setting the parameter to either StringComparison.Ordinal or StringComparison.OrdinalIgnoreCase, your code often gains speed, becomes more correct, and becomes more reliable.</span></span>|
|[<span data-ttu-id="df776-124">CA1310：指定 StringComparison 以提升正確性</span><span class="sxs-lookup"><span data-stu-id="df776-124">CA1310: Specify StringComparison for correctness</span></span>](ca1310.md)|<span data-ttu-id="df776-125">字串比較作業會使用未設定 StringComparison 參數的方法多載，並預設使用特定文化特性的字串比較。</span><span class="sxs-lookup"><span data-stu-id="df776-125">A string comparison operation uses a method overload that does not set a StringComparison parameter and uses culture-specific string comparison by default.</span></span>|
|[<span data-ttu-id="df776-126">CA2101 必須：指定 P/Invoke 字串引數的封送處理</span><span class="sxs-lookup"><span data-stu-id="df776-126">CA2101: Specify marshaling for P/Invoke string arguments</span></span>](ca2101.md)|<span data-ttu-id="df776-127">平台叫用成員允許部分信任的呼叫端、具有字串參數，且不會明確地封送處理字串。</span><span class="sxs-lookup"><span data-stu-id="df776-127">A platform invoke member allows for partially trusted callers, has a string parameter, and does not explicitly marshal the string.</span></span> <span data-ttu-id="df776-128">這樣會造成安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="df776-128">This can cause a potential security vulnerability.</span></span>|
