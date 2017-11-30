---
title: "型別提供者疑難排解"
description: "探索可能的解決方案，當您使用 F # 中的型別提供者時遇到最常見的問題。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 44533045-9862-43c5-81d9-3e05157e975a
ms.openlocfilehash: 2b54454d7950dfdd6512d849fd739f505ef3317d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="troubleshooting-type-providers"></a>型別提供者疑難排解

本主題描述，並提供可能的解決方案會使用型別提供者時遇到最常見的問題。


## <a name="possible-problems-with-type-providers"></a>可能發生問題的型別提供者
如果您遇到問題，當您使用型別提供者時，您可以檢閱下表針對最常見的解決方案。



|問題|建議的動作|
|-------|-----------------|
|**結構描述變更**。 最適合的資料來源結構描述的型別提供者工作很穩定。 如果您新增資料表或資料行，或對該結構描述進行其他變更，型別提供者無法自動辨識這些變更。|清除或重建專案。 若要清除專案，選擇 **建置**，**清除** *ProjectName*功能表列上。 若要重建專案，選擇 **建置**，**重建** *ProjectName*功能表列上。 這些動作會重設所有型別提供者的狀態，並強制重新連線至資料來源，並取得更新的結構描述資訊提供者。|
|**連線失敗**。 不正確的 URL 或連接字串、 網路已關閉，或資料來源或服務無法使用。|Web 服務或 OData 服務，您可以嘗試驗證 URL 是否正確，且該服務的 Internet Explorer 中的 URL。 資料庫連接字串，您可以使用中的資料連接工具**伺服器總管**驗證是否連接字串無效，而且資料庫可供使用。 還原您的連線之後，您應該也要清除或重建專案，讓型別提供者會重新連線到網路。|
|**不是有效的認證**。 您必須擁有資料來源或 web 服務的有效權限。|SQL 連接，使用者名稱和連接字串或組態檔中指定的密碼必須是有效的資料庫。 如果您使用 Windows 驗證，您必須具有資料庫的存取權。 資料庫管理員可以識別所需的權限存取每個資料庫和資料庫內的每個項目。<br /><br />Web 服務或資料服務，您必須具有適當認證。 大部分的型別提供者提供 DataContext 物件，其中包含您可以設定為適當的使用者名稱和存取金鑰的認證屬性。|
|**不是有效的路徑**。 檔案的路徑無效。|請確認路徑是否正確，且檔案存在。 此外，您必須加上引號的路徑中任何 backlashes 正確，或使用逐字字串或三重括住的字串。|

## <a name="see-also"></a>另請參閱
[類型提供者](index.md)
