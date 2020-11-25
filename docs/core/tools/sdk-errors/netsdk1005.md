---
title: NETSDK1005 和 NETSDK1047：資產檔案遺失目標
description: 如何解決資產檔案遺失目標的問題。
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 207c8b0274c13e7af594e05cfac2a95907f85b81
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717899"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a>NETSDK1005 和 NETSDK1047：資產檔案遺失目標

本文 **適用于：** ✔️ .net CORE 2.1.100 SDK 和更新版本

當 .NET SDK 發出錯誤 NETSDK1005 或 NETSDK1047 時，專案的資產檔案就會遺失其中一個目標 framework 的相關資訊。 通常可以藉由確保執行還原，而遺漏的目標值包含在專案的屬性中，來修正此問題 `TargetFrameworks` 。

> [!NOTE]
> 當 .NET 5 preview 8 的早期版本搭配使用時，有一個已知的問題，就是與導致此錯誤的 Visual Studio 16.8 預覽版本搭配使用。 具體而言，如果遺漏的目標是 `net5.0-windows7.0` 或 `net5.0` ，請確定您已更新為最新版本的 Visual Studio 和 .NET 5 SDK。
