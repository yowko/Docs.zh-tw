---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 9235f1bcda7529b71aef542d3a49da08a9d4b59e
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "96585143"
---
<span data-ttu-id="85e44-101">在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。</span><span class="sxs-lookup"><span data-stu-id="85e44-101">Insecure deserializers are vulnerable when deserializing untrusted data.</span></span> <span data-ttu-id="85e44-102">攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。</span><span class="sxs-lookup"><span data-stu-id="85e44-102">An attacker could modify the serialized data to include unexpected types to inject objects with malicious side effects.</span></span> <span data-ttu-id="85e44-103">針對不安全的還原序列化程式進行攻擊，例如，在基礎作業系統上執行命令、透過網路進行通訊，或刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="85e44-103">An attack against an insecure deserializer could, for example, execute commands on the underlying operating system, communicate over the network, or delete files.</span></span>
