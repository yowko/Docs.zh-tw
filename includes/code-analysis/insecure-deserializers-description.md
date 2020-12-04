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
在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 針對不安全的還原序列化程式進行攻擊，例如，在基礎作業系統上執行命令、透過網路進行通訊，或刪除檔案。
