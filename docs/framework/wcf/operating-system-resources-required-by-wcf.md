---
title: WCF 所需的作業系統資源
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: c2c26d769424a8d0655591cb10b4b13df8a15884
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961140"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="916ee-102">WCF 所需的作業系統資源</span><span class="sxs-lookup"><span data-stu-id="916ee-102">Operating System Resources Required by WCF</span></span>

<span data-ttu-id="916ee-103">Windows Communication Foundation （WCF）相依于作業系統所提供的多項資源以運作。</span><span class="sxs-lookup"><span data-stu-id="916ee-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="916ee-104">下表列出這些資源：</span><span class="sxs-lookup"><span data-stu-id="916ee-104">The following table lists those resources:</span></span>

|<span data-ttu-id="916ee-105">資源</span><span class="sxs-lookup"><span data-stu-id="916ee-105">Resource</span></span>|<span data-ttu-id="916ee-106">描述</span><span class="sxs-lookup"><span data-stu-id="916ee-106">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="916ee-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="916ee-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="916ee-108">支援 OleTx 異動時需要。</span><span class="sxs-lookup"><span data-stu-id="916ee-108">Required to support OleTx transactions.</span></span>|
|<span data-ttu-id="916ee-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="916ee-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="916ee-110">如果您要使用 IIS 裝載應用程式時需要。</span><span class="sxs-lookup"><span data-stu-id="916ee-110">Required if you want to use IIS to host your application.</span></span>|
|<span data-ttu-id="916ee-111">Windows Process Activation Service (WAS)</span><span class="sxs-lookup"><span data-stu-id="916ee-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="916ee-112">如果您要使用 WAS 裝載應用程式時需要。</span><span class="sxs-lookup"><span data-stu-id="916ee-112">Required if you want to use WAS to host your application.</span></span>|
