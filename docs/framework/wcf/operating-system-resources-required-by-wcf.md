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
# <a name="operating-system-resources-required-by-wcf"></a>WCF 所需的作業系統資源

Windows Communication Foundation （WCF）相依于作業系統所提供的多項資源以運作。 下表列出這些資源：

|資源|描述|
|--------------|-----------------|
|Microsoft Distributed Transaction Coordinator (MSDTC)|支援 OleTx 異動時需要。|
|Internet Information Services (IIS)|如果您要使用 IIS 裝載應用程式時需要。|
|Windows Process Activation Service (WAS)|如果您要使用 WAS 裝載應用程式時需要。|
