---
title: 使用指數輪詢來實作重試
description: 了解如何使用指數輪詢來實作重試。
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674535"
---
# <a name="implement-retries-with-exponential-backoff"></a>使用指數輪詢來實作重試

[*使用指數輪詢重試*](/azure/architecture/patterns/retry)是重試某個作業，並呈指數增加等候時間，直到達到最大重試計數的技術 ([Exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff) (指數輪詢))。 這項技術體認到雲端資源可能會基於任何原因而斷斷續續無法使用超過好幾秒。 例如，協調器可能正在將某個容器移至叢集中的另一個節點進行負載平衡。 在這段期間，部分要求可能會失敗。 另一個範例可能是 SQL Azure 之類的資料庫，其中某個資料庫可能移至另一部伺服器進行負載平衡，而導致資料庫無法使用好幾秒。

使用指數輪詢來實作重試邏輯的方法有許多種。

>[!div class="step-by-step"]
>[上一頁](partial-failure-strategies.md)
>[下一頁](implement-resilient-entity-framework-core-sql-connections.md)
