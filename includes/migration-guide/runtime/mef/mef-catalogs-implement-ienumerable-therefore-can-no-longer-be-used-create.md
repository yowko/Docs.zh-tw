---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235162"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.5 開始，MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式 (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> 物件)。 嘗試序列化 MEF 目錄會擲回例外狀況。|
|建議|無法再使用 MEF 建立序列化程式|
|範圍|主要|
|版本|4.5|
|類型|執行階段|
