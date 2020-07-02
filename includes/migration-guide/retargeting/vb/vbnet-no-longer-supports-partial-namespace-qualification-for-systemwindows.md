---
ms.openlocfilehash: cef8096c971da8ae245ff974697022f350cb9195
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616032"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET 不再支援 System.Windows API 的部分命名空間限定性條件

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5.2 開始，VB.NET 專案無法以部分限定的命名空間來指定 System.Windows API。 例如，參考 `Windows.Forms.DialogResult` 將會失敗。 相反地，程式碼必須參考完整名稱 (<xref:System.Windows.Forms.DialogResult>)，或匯入特定命名空間並只參考 <xref:System.Windows.Forms.DialogResult?displayProperty=fullName>。

#### <a name="suggestion"></a>建議

您應該更新程式碼，以簡單名稱 (並匯入相關命名空間) 或完整名稱參考 `System.Windows` API。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.5.2       |
| 類型    | 正在重定目標 |
