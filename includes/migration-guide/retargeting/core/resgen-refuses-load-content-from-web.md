---
ms.openlocfilehash: f980c8029375074889505a8eb7e8a65aaa8d74e4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614368"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a>Resgen 拒絕從 web 載入內容

#### <a name="details"></a>詳細資料

.resx 檔案可能包含二進位格式的輸入。 如果您嘗試使用 resgen 來載入從不受信任位置下載的檔案，預設將無法載入輸入。

#### <a name="suggestion"></a>建議

需要從不受信任的位置載入二進位格式輸入的 Resgen 使用者，可以從輸入檔移除 web 標記，或套用退出怪癖。新增下列登錄設定，以套用全電腦的退出怪癖： [HKEY_LOCAL_MACHINE \software\microsoft.netframework\sdk] &quot; AllowProcessOfUntrustedResourceFiles &quot; = &quot; true&quot;

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |
