---
title: 對等名稱和 PNRP 識別碼
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
ms.openlocfilehash: e7e92519bede478a5e26a88a56236f987c93c441
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772904"
---
# <a name="peer-names-and-pnrp-ids"></a><span data-ttu-id="ab95d-102">對等名稱和 PNRP 識別碼</span><span class="sxs-lookup"><span data-stu-id="ab95d-102">Peer Names and PNRP IDs</span></span>
<span data-ttu-id="ab95d-103">對等名稱代表通訊端點，可以是一部電腦、一位使用者、一個群組、一項服務，或是與可解析成 IPv6 位址之對等建立關聯的任何項目。</span><span class="sxs-lookup"><span data-stu-id="ab95d-103">A Peer Name represents an endpoint for communication, which can be a computer, a user, a group, a service, or anything associated with a Peer that can be resolved to an IPv6 address.</span></span> <span data-ttu-id="ab95d-104">對等名稱解析通訊協定 (PNRP) 採用靜態上唯一的對等名稱來建立 PNRP 識別碼，以用來識別雲端成員。</span><span class="sxs-lookup"><span data-stu-id="ab95d-104">The Peer Name Resolution Protocol (PNRP) takes the statistically unique Peer Name for the creation of a PNRP ID, which is used to identify cloud members.</span></span>  
  
## <a name="peer-names"></a><span data-ttu-id="ab95d-105">對等名稱</span><span class="sxs-lookup"><span data-stu-id="ab95d-105">Peer Names</span></span>  
 <span data-ttu-id="ab95d-106">對等名稱可以註冊為不安全或安全的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab95d-106">Peer names can be registered as unsecured or secured.</span></span> <span data-ttu-id="ab95d-107">不安全的名稱是指單純為文字字串的名稱，容易受到詐騙，因為任何人都可以註冊重複的不安全名稱。</span><span class="sxs-lookup"><span data-stu-id="ab95d-107">Unsecured names are just text strings that are subject to spoofing, as anyone can register a duplicate unsecured name.</span></span> <span data-ttu-id="ab95d-108">不安全的名稱最好用於私人或是受保護的網路中。</span><span class="sxs-lookup"><span data-stu-id="ab95d-108">Unsecured names are best used in private or otherwise protected networks.</span></span> <span data-ttu-id="ab95d-109">安全的名稱是使用憑證和數位簽章進行保護。</span><span class="sxs-lookup"><span data-stu-id="ab95d-109">Secured names are protected with a certificate and a digital signature.</span></span> <span data-ttu-id="ab95d-110">只有原始發行者才能證明安全名稱的擁有權。</span><span class="sxs-lookup"><span data-stu-id="ab95d-110">Only the original publisher will be able to prove ownership of a secured name.</span></span>  
  
 <span data-ttu-id="ab95d-111">雲端與範圍的組合提供參與 PNRP 活動的對等相當安全的環境。</span><span class="sxs-lookup"><span data-stu-id="ab95d-111">The combination of cloud and scope provides a reasonably secure environment for peers that participate in PNRP activity.</span></span> <span data-ttu-id="ab95d-112">不過，使用安全的對等名稱不保證網路應用程式的整體安全性。</span><span class="sxs-lookup"><span data-stu-id="ab95d-112">However, using a secured peer name does not ensure the overall security of the networking application.</span></span> <span data-ttu-id="ab95d-113">應用程式的安全性是與實作相依。</span><span class="sxs-lookup"><span data-stu-id="ab95d-113">Security of the application is implementation-dependent.</span></span>  
  
 <span data-ttu-id="ab95d-114">安全的對等名稱只能由其擁有者註冊，並以公開金鑰加密進行保護。</span><span class="sxs-lookup"><span data-stu-id="ab95d-114">Secured peer names are only registered by their owner and are protected with public key cryptography.</span></span> <span data-ttu-id="ab95d-115">安全的對等名稱是為由具有對應私密金鑰的對等實體所擁有。</span><span class="sxs-lookup"><span data-stu-id="ab95d-115">A secured peer name is considered owned by the peer entity having the corresponding private key.</span></span> <span data-ttu-id="ab95d-116">擁有權可以透過使用私密金鑰簽署的認證對等位址 (CPA) 進行證明。</span><span class="sxs-lookup"><span data-stu-id="ab95d-116">Ownership can be proved via the certified peer address (CPA), which is signed using the private key.</span></span> <span data-ttu-id="ab95d-117">惡意使用者沒有對應的私密金鑰，就無法偽造對等名稱的擁有權。</span><span class="sxs-lookup"><span data-stu-id="ab95d-117">A malicious user cannot forge ownership of a peer name without the corresponding private key.</span></span>  
  
## <a name="pnrp-ids"></a><span data-ttu-id="ab95d-118">PNRP 識別碼</span><span class="sxs-lookup"><span data-stu-id="ab95d-118">PNRP IDs</span></span>  
 <span data-ttu-id="ab95d-119">![PNRP 識別碼](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")</span><span class="sxs-lookup"><span data-stu-id="ab95d-119">![PNRP ID](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")</span></span>  
  
 <span data-ttu-id="ab95d-120">PNRP 識別碼由下列各項所組成：</span><span class="sxs-lookup"><span data-stu-id="ab95d-120">PNRP IDs are composed of the following:</span></span>  
  
-   <span data-ttu-id="ab95d-121">高序位 128 位元 (稱為對等 (P2P) 識別碼) 是指派給端點的對等名稱雜湊。</span><span class="sxs-lookup"><span data-stu-id="ab95d-121">The high-order 128 bits, known as the peer-to-peer (P2P) ID, are a hash of a peer name assigned to the endpoint.</span></span> <span data-ttu-id="ab95d-122">對等名稱的格式如下：*Authority.Classifier*。</span><span class="sxs-lookup"><span data-stu-id="ab95d-122">The peer name has the following format: *Authority.Classifier*.</span></span> <span data-ttu-id="ab95d-123">安全名稱的 *Authority* 是以十六進位字元表示，是對等名稱公開金鑰的安全雜湊演算法 1 (SHA1) 雜湊。</span><span class="sxs-lookup"><span data-stu-id="ab95d-123">For secured names, *Authority* is the Secure Hash Algorithm 1 (SHA1) hash of the public key of the peer name in hexadecimal characters.</span></span> <span data-ttu-id="ab95d-124">不安全名稱的 *Authority* 則為單一字元 "0"。</span><span class="sxs-lookup"><span data-stu-id="ab95d-124">For unsecured names, the *Authority* is the single character "0".</span></span> <span data-ttu-id="ab95d-125">*Classifier* 是識別應用程式的字串。</span><span class="sxs-lookup"><span data-stu-id="ab95d-125">*Classifier* is a string that identifies the application.</span></span> <span data-ttu-id="ab95d-126">對等名稱分類器的長度不能超過 149 個字元 (包含 `null` 結束字元)。</span><span class="sxs-lookup"><span data-stu-id="ab95d-126">No peer name classifier can be greater than 149 characters long, including the `null` terminator.</span></span>  
  
-   <span data-ttu-id="ab95d-127">低序位 128 位元用於表示服務位置所產生的數字，用來識別相同雲端中同一個 P2P 識別碼的不同執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab95d-127">The low-order 128 bits are used for the Service Location, which is a generated number that identifies different instances of the same P2P ID in the same cloud.</span></span>  
  
 <span data-ttu-id="ab95d-128">這個 P2P 識別碼與服務位置的組合可讓單一電腦登錄多個 PNRP 識別碼。</span><span class="sxs-lookup"><span data-stu-id="ab95d-128">This combination of P2P ID and Service Location allows multiple PNRP IDs to be registered from a single computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab95d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab95d-129">See also</span></span>

- <xref:System.Net.PeerToPeer.PeerName>
- <xref:System.Net.PeerToPeer>
