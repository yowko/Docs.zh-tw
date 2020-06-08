---
title: IPv6 定址
description: 瞭解網際網路通訊協定第6版（IPv6）位址，包括文字標記法和網址類別型。
ms.date: 03/30/2017
helpviewer_keywords:
- Internet Protocol version 6, addresses in
- Neighbor Discovery
- IPv6, enabling
- IPv6, mobility and
- Internet Protocol version 6, anycast addresses
- IPv6, Neighbor Discovery
- Internet Protocol version 6, auto-configuring
- Internet Protocol version 6, enabling
- IPv6, unicast addresses
- IPv6, auto-configuring
- Internet Protocol version 6, routing
- IPv6, RFC documents
- IPv6, routing
- Internet Protocol version 6, disabling
- Internet Protocol version 6, unicast addresses
- IPv6, multicast addresses
- Internet Protocol version 6, mobility and
- Internet Protocol version 6, RFC documents
- Internet Protocol version 6, Neighbor Discovery
- IPv6, anycast addresses
- Internet Protocol version 6, multicast addresses
- IPv6, addresses in
- IPv6, disabling
ms.assetid: 20a104ae-1649-4649-a005-531a5cf74c93
ms.openlocfilehash: fbf68cb5f40450c2f9ecf4900801ee55e326fcb4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502336"
---
# <a name="ipv6-addressing"></a><span data-ttu-id="247be-103">IPv6 定址</span><span class="sxs-lookup"><span data-stu-id="247be-103">IPv6 Addressing</span></span>

<span data-ttu-id="247be-104">網際網路通訊協定第 6 版 (IPv6) 的位址長度為 128 個位元長。</span><span class="sxs-lookup"><span data-stu-id="247be-104">In the Internet Protocol version 6 (IPv6), addresses are 128 bits long.</span></span> <span data-ttu-id="247be-105">使用這類大型位址空間的其中一個原因是，將可用的位址細分到路由網域的階層，反映網際網路的拓撲。</span><span class="sxs-lookup"><span data-stu-id="247be-105">One reason for such a large address space is to subdivide the available addresses into a hierarchy of routing domains that reflect the Internet's topology.</span></span> <span data-ttu-id="247be-106">另一個原因是，將連線裝置之網路網路介面卡 (或介面) 的位址對應至網路。</span><span class="sxs-lookup"><span data-stu-id="247be-106">Another reason is to map the addresses of network adapters (or interfaces) that connect devices to the network.</span></span> <span data-ttu-id="247be-107">IPv6 特有的固有功能，是在其最低層級解析位址，即網路介面層級，且也擁有自動組態功能。</span><span class="sxs-lookup"><span data-stu-id="247be-107">IPv6 features an inherent capability to resolve addresses at their lowest level, which is at the network interface level, and also has auto-configuration capabilities.</span></span>

## <a name="text-representation"></a><span data-ttu-id="247be-108">文字表示法</span><span class="sxs-lookup"><span data-stu-id="247be-108">Text Representation</span></span>

<span data-ttu-id="247be-109">下列是三種使用文字字串表示 IPv6 位址的慣例格式：</span><span class="sxs-lookup"><span data-stu-id="247be-109">The following are the three conventional forms used to represent the IPv6 addresses as text strings:</span></span>

- <span data-ttu-id="247be-110">**冒號:十六進位格式**。</span><span class="sxs-lookup"><span data-stu-id="247be-110">**Colon-hexadecimal form**.</span></span> <span data-ttu-id="247be-111">這是慣用的格式 n:n:n:n:n:n:n:n。</span><span class="sxs-lookup"><span data-stu-id="247be-111">This is the preferred form n:n:n:n:n:n:n:n.</span></span> <span data-ttu-id="247be-112">每個 n 代表位址的八個 16 位元項目的一個十六進位值。</span><span class="sxs-lookup"><span data-stu-id="247be-112">Each n represents the hexadecimal value of one of the eight 16-bit elements of the address.</span></span> <span data-ttu-id="247be-113">例如： `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562` 。</span><span class="sxs-lookup"><span data-stu-id="247be-113">For example: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.</span></span>

- <span data-ttu-id="247be-114">**壓縮格式**。</span><span class="sxs-lookup"><span data-stu-id="247be-114">**Compressed form**.</span></span> <span data-ttu-id="247be-115">因為位址長度的原因，位址通常會包含由零組成的長字串。</span><span class="sxs-lookup"><span data-stu-id="247be-115">Due to the address length, it is common to have addresses containing a long string of zeros.</span></span> <span data-ttu-id="247be-116">若要簡化撰寫這些地址，請使用壓縮格式，其中單一連續序列的 0 區塊會以雙冒號符號 (::) 表示。</span><span class="sxs-lookup"><span data-stu-id="247be-116">To simplify writing these addresses, use the compressed form, in which a single contiguous sequence of 0 blocks are represented by a double-colon symbol (::).</span></span> <span data-ttu-id="247be-117">這個符號在位址中只會出現一次。</span><span class="sxs-lookup"><span data-stu-id="247be-117">This symbol can appear only once in an address.</span></span> <span data-ttu-id="247be-118">例如，多點傳送位址 `FFED:0:0:0:0:BA98:3210:4562` 的壓縮格式是 `FFED::BA98:3210:4562`。</span><span class="sxs-lookup"><span data-stu-id="247be-118">For example, the multicast address `FFED:0:0:0:0:BA98:3210:4562` in compressed form is `FFED::BA98:3210:4562`.</span></span> <span data-ttu-id="247be-119">單點傳播位址 `3FFE:FFFF:0:0:8:800:20C4:0` 的壓縮格式是 `3FFE:FFFF::8:800:20C4:0`。</span><span class="sxs-lookup"><span data-stu-id="247be-119">The unicast address `3FFE:FFFF:0:0:8:800:20C4:0` in compressed form is `3FFE:FFFF::8:800:20C4:0`.</span></span> <span data-ttu-id="247be-120">回送位址 `0:0:0:0:0:0:0:1` 的壓縮格式是 `::`1。</span><span class="sxs-lookup"><span data-stu-id="247be-120">The loopback address `0:0:0:0:0:0:0:1` in compressed form is `::`1.</span></span> <span data-ttu-id="247be-121">未指定的位址 `0:0:0:0:0:0:0:0` 的壓縮格式是 `::`。</span><span class="sxs-lookup"><span data-stu-id="247be-121">The unspecified address `0:0:0:0:0:0:0:0` in compressed form is `::`.</span></span>

- <span data-ttu-id="247be-122">**混合格式**。</span><span class="sxs-lookup"><span data-stu-id="247be-122">**Mixed form**.</span></span> <span data-ttu-id="247be-123">這種格式結合了 IPv4 和 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="247be-123">This form combines IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="247be-124">在此情況下，位址格式是 n:n:n:n:n:n:d.d.d.d，每個 n 代表六個 IPv6 高序位 16 位元位址項目的十六進位值，每個 d 代表 IPv4 位址的十進位值。</span><span class="sxs-lookup"><span data-stu-id="247be-124">In this case, the address format is n:n:n:n:n:n:d.d.d.d, where each n represents the hexadecimal values of the six IPv6 high-order 16-bit address elements, and each d represents the decimal value of an IPv4 address.</span></span>

## <a name="address-types"></a><span data-ttu-id="247be-125">位址類型</span><span class="sxs-lookup"><span data-stu-id="247be-125">Address Types</span></span>

<span data-ttu-id="247be-126">位址中的前置位元會定義特定的 IPv6 位址類型。</span><span class="sxs-lookup"><span data-stu-id="247be-126">The leading bits in the address define the specific IPv6 address type.</span></span> <span data-ttu-id="247be-127">包含這些前置位元的變數長度欄位稱為格式首碼 (FP)。</span><span class="sxs-lookup"><span data-stu-id="247be-127">The variable-length field containing these leading bits is called a Format Prefix (FP).</span></span>

<span data-ttu-id="247be-128">IPv6 單點傳播位址分為兩個部分。</span><span class="sxs-lookup"><span data-stu-id="247be-128">An IPv6 unicast address is divided into two parts.</span></span> <span data-ttu-id="247be-129">第一個部分包含位址前置詞，第二個部分包含介面識別碼。</span><span class="sxs-lookup"><span data-stu-id="247be-129">The first part contains the address prefix, and the second part contains the interface identifier.</span></span> <span data-ttu-id="247be-130">表示 IPv6 位址/前置詞組合的簡潔方式如下：ipv6 位址/前置詞長度。</span><span class="sxs-lookup"><span data-stu-id="247be-130">A concise way to express an IPv6 address/prefix combination is as follows: ipv6-address/prefix-length.</span></span>

<span data-ttu-id="247be-131">下例是具有 64 位元前置詞的位址。</span><span class="sxs-lookup"><span data-stu-id="247be-131">The following is an example of an address with a 64-bit prefix.</span></span>

<span data-ttu-id="247be-132">`3FFE:FFFF:0:CD30:0:0:0:0/64`.</span><span class="sxs-lookup"><span data-stu-id="247be-132">`3FFE:FFFF:0:CD30:0:0:0:0/64`.</span></span>

<span data-ttu-id="247be-133">本例中的前置詞為 `3FFE:FFFF:0:CD30`。</span><span class="sxs-lookup"><span data-stu-id="247be-133">The prefix in this example is `3FFE:FFFF:0:CD30`.</span></span> <span data-ttu-id="247be-134">位址也可以壓縮格式寫入，如 `3FFE:FFFF:0:CD30::/64`。</span><span class="sxs-lookup"><span data-stu-id="247be-134">The address can also be written in a compressed form, as `3FFE:FFFF:0:CD30::/64`.</span></span>

<span data-ttu-id="247be-135">IPv6 會定義下列位址類型：</span><span class="sxs-lookup"><span data-stu-id="247be-135">IPv6 defines the following address types:</span></span>

- <span data-ttu-id="247be-136">**單點傳播位址**。</span><span class="sxs-lookup"><span data-stu-id="247be-136">**Unicast address**.</span></span> <span data-ttu-id="247be-137">單一介面的識別碼。</span><span class="sxs-lookup"><span data-stu-id="247be-137">An identifier for a single interface.</span></span> <span data-ttu-id="247be-138">傳送到此位址的封包會被傳遞到已識別的介面。</span><span class="sxs-lookup"><span data-stu-id="247be-138">A packet sent to this address is delivered to the identified interface.</span></span> <span data-ttu-id="247be-139">單點傳播位址是高序位八位元值從多點傳送位址中區隔出來的。</span><span class="sxs-lookup"><span data-stu-id="247be-139">The unicast addresses are distinguished from the multicast addresses by the value of the high-order octet.</span></span> <span data-ttu-id="247be-140">多點傳送位址之高序位八位元的十六進位值為 FF。</span><span class="sxs-lookup"><span data-stu-id="247be-140">The multicast addresses' high-order octet has the hexadecimal value of FF.</span></span> <span data-ttu-id="247be-141">此八位元的任何其他值會識別單點傳播位址。</span><span class="sxs-lookup"><span data-stu-id="247be-141">Any other value for this octet identifies a unicast address.</span></span> <span data-ttu-id="247be-142">以下是不同類型的單點傳播位址：</span><span class="sxs-lookup"><span data-stu-id="247be-142">The following are different types of unicast addresses:</span></span>

  - <span data-ttu-id="247be-143">**連結-本機位址**。</span><span class="sxs-lookup"><span data-stu-id="247be-143">**Link-local addresses**.</span></span> <span data-ttu-id="247be-144">這些位址是用在單一連結，且具有下列格式：FE80::*InterfaceID*。</span><span class="sxs-lookup"><span data-stu-id="247be-144">These addresses are used on a single link and have the following format: FE80::*InterfaceID*.</span></span> <span data-ttu-id="247be-145">連結上的節點之間在處理自動位址組態、鄰居探索，或沒有路由器時，會使用連結-本機位址。</span><span class="sxs-lookup"><span data-stu-id="247be-145">Link-local addresses are used between nodes on a link for auto-address configuration, neighbor discovery, or when no routers are present.</span></span> <span data-ttu-id="247be-146">連結-本機位址主要是用在啟動時，以及系統尚未取得較大範圍的位址時。</span><span class="sxs-lookup"><span data-stu-id="247be-146">A link-local address is used primarily at startup and when the system has not yet acquired addresses of larger scope.</span></span>

  - <span data-ttu-id="247be-147">**網站-本機位址**。</span><span class="sxs-lookup"><span data-stu-id="247be-147">**Site-local addresses**.</span></span> <span data-ttu-id="247be-148">這些位址是用在單一網站，且具有下列格式：FEC0::*SubnetID*:*InterfaceID*。</span><span class="sxs-lookup"><span data-stu-id="247be-148">These addresses are used on a single site and have the following format: FEC0::*SubnetID*:*InterfaceID*.</span></span> <span data-ttu-id="247be-149">網站-本機位址可用來在網站中定址，不需要全域前置詞。</span><span class="sxs-lookup"><span data-stu-id="247be-149">The site-local addresses are used for addressing inside a site without the need for a global prefix.</span></span>

  - <span data-ttu-id="247be-150">**全域 IPv6 單點傳播位址**。</span><span class="sxs-lookup"><span data-stu-id="247be-150">**Global IPv6 unicast addresses**.</span></span> <span data-ttu-id="247be-151">這些位址可以用在整個網際網路上，而且具有下列格式：010(FP，3 位元) TLA ID (13 位元) 保留項目 (8 位元) NLA ID (24 位元) SLA ID (16 位元) *InterfaceID* (64 位元)。</span><span class="sxs-lookup"><span data-stu-id="247be-151">These addresses can be used across the Internet and have the following format: 010(FP, 3 bits) TLA ID (13 bits) Reserved (8 bits) NLA ID (24 bits) SLA ID (16 bits) *InterfaceID* (64 bits).</span></span>

- <span data-ttu-id="247be-152">**多點傳送位址**。</span><span class="sxs-lookup"><span data-stu-id="247be-152">**Multicast address**.</span></span> <span data-ttu-id="247be-153">一組介面 (通常屬於不同的節點) 的識別碼。</span><span class="sxs-lookup"><span data-stu-id="247be-153">An identifier for a set of interfaces (typically belonging to different nodes).</span></span> <span data-ttu-id="247be-154">傳送到此位址的封包會被傳遞到該位址所識別的所有介面。</span><span class="sxs-lookup"><span data-stu-id="247be-154">A packet sent to this address is delivered to all the interfaces identified by the address.</span></span> <span data-ttu-id="247be-155">多點傳送位址類型取代 IPv4 廣播位址。</span><span class="sxs-lookup"><span data-stu-id="247be-155">The multicast address types supersede the IPv4 broadcast addresses.</span></span>

- <span data-ttu-id="247be-156">**任一傳播位址**。</span><span class="sxs-lookup"><span data-stu-id="247be-156">**Anycast address**.</span></span> <span data-ttu-id="247be-157">一組介面 (通常屬於不同的節點) 的識別碼。</span><span class="sxs-lookup"><span data-stu-id="247be-157">An identifier for a set of interfaces (typically belonging to different nodes).</span></span> <span data-ttu-id="247be-158">傳送到此位址的封包只會被傳遞該位址所識別的一個介面。</span><span class="sxs-lookup"><span data-stu-id="247be-158">A packet sent to this address is delivered to only one interface identified by the address.</span></span> <span data-ttu-id="247be-159">這是路由計量所識別的最近介面。</span><span class="sxs-lookup"><span data-stu-id="247be-159">This is the nearest interface as identified by routing metrics.</span></span> <span data-ttu-id="247be-160">任一傳播位址皆是取自單點傳播位址空間，而且語法上沒有分別。</span><span class="sxs-lookup"><span data-stu-id="247be-160">Anycast addresses are taken from the unicast address space and are not syntactically distinguishable.</span></span> <span data-ttu-id="247be-161">位址介面會將單點傳播與任一傳播位址之間的差異當成其組態的函式執行。</span><span class="sxs-lookup"><span data-stu-id="247be-161">The addressed interface performs the distinction between unicast and anycast addresses as a function of its configuration.</span></span>

<span data-ttu-id="247be-162">一般情況下，節點一律會有連結-本機位址。</span><span class="sxs-lookup"><span data-stu-id="247be-162">In general, a node always has a link-local address.</span></span> <span data-ttu-id="247be-163">它可能有網站-本機位址和一或多個全域位址。</span><span class="sxs-lookup"><span data-stu-id="247be-163">It might have a site-local address and one or more global addresses.</span></span>

## <a name="see-also"></a><span data-ttu-id="247be-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="247be-164">See also</span></span>

- [<span data-ttu-id="247be-165">網際網路通訊協定第6版</span><span class="sxs-lookup"><span data-stu-id="247be-165">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="247be-166">通訊端</span><span class="sxs-lookup"><span data-stu-id="247be-166">Sockets</span></span>](sockets.md)
