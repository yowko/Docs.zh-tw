---
title: NETSDK1059：專案包含過時的 .NET CLI 工具
description: 如何解決包含過時 .NET CLI 工具之專案的問題。
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1059
ms.openlocfilehash: 2960b9255dab9e61a84e49bc029666753d8c9a1e
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957138"
---
# <a name="netsdk1059-project-contains-obsolete-net-cli-tool"></a>NETSDK1059：專案包含過時的 .NET CLI 工具

本文**適用于：** ✔️ .NET 2.1.100 SDK 和更新版本

當 .NET SDK 發出警告 NETSDK1059 時，您的專案會包含過時的 .NET CLI 工具。 從 .NET 2.1，這些工具都包含在 .NET SDK 中，而且不需要由專案明確參考。 如需遷移至 .NET 2.1 的詳細資訊，請參閱 [這裡](https://aka.ms/dotnetclitools-in-box)。
