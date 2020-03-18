---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567768"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>"C"地區設定映射到不變地區設定

.NET Core 2.2 和早期版本取決於預設 ICU 行為，該行為將"C"地區設定映射到en_US_POSIX地區設定。 en_US_POSIX地區設定具有不可取的整理行為，因為它不支援不區分大小寫的字串比較。 由於某些 Linux 發行版本將"C"地區設定設置為預設區域設置，因此使用者遇到意外行為。

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0 開始，"C"地區設定映射已更改為使用不變數地區設定，而不是en_US_POSIX。 "C"地區設定到不變數映射也應用於 Windows 以保持一致性。

將"C"映射到en_US_POSIX區域性會導致客戶混淆，因為en_US_POSIX不支援不區分大小寫的排序/搜索字串操作。 由於"C"地區設定在某些 Linux 發行版本中用作預設區域設置，因此客戶在這些作業系統上遇到這種不希望的行為。

#### <a name="version-introduced"></a>介紹的版本

3.0

### <a name="recommended-action"></a>建議的動作

沒有什麼比對這種變化的認識更具體了。 此更改僅影響使用"C"地區設定映射的應用程式。

### <a name="category"></a>類別

全球化

### <a name="affected-apis"></a>受影響的 API

所有排序規則和文化 API 都受此更改的影響。

<!--

-->
