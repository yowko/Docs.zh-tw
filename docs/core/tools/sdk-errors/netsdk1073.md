---
title: NETSDK1073：無法辨識 FrameworkReference
description: 如何解決找不到 FrameworkReference 的問題。
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1073
ms.openlocfilehash: 59b5f63dcfe0115feabc2d87d24a09c6a650cc62
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957137"
---
# <a name="netsdk1073-the-frameworkreference-was-not-recognized"></a>NETSDK1073：無法辨識 FrameworkReference

本文**適用于：** ✔️ .NET 2.1.100 SDK 和更新版本

此錯誤通常表示 SDK 找不到特定的 FrameworkReference 版本。 請嘗試刪除您的 *obj* 和 *bin* 資料夾並執行， `dotnet restore` 以重新下載最新的目標套件。

或者，您的安裝可能有問題，因此請確定您是使用最新版本的 .NET 並 Visual Studio
