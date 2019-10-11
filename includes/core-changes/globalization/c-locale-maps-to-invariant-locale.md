---
ms.openlocfilehash: f9ae32c44e5648eb74d7eab9fa5aa6cc2f17b9a1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237317"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>"C" 地區設定對應到不變的地區設定

.NET Core 2.2 和更早版本取決於預設的 ICU 行為，這會將 "C" 地區設定對應至 en_US_POSIX 地區設定。 En_US_POSIX 地區設定有不想要的定序行為，因為它不支援不區分大小寫的字串比較。 由於某些 Linux 散發套件會將 "C" 地區設定設為預設地區設定，因此使用者會遇到非預期的行為。 

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0 開始，"C" 地區設定對應已變更為使用不變的地區設定，而不是 en_US_POSIX。 非變異對應的 "C" 地區設定也會套用至 Windows 以保持一致性。

將 "C" 對應至 en_US_POSIX 文化特性會造成客戶混淆，因為 en_US_POSIX 不支援不區分大小寫的排序/搜尋字串作業。 因為在某些 Linux 散發版本中，會使用 "C" 地區設定做為預設地區設定，所以客戶會在這些作業系統上遇到此不想要的行為。 

#### <a name="version-introduced"></a>引進的版本

3.0

### <a name="recommended-action"></a>建議的動作

除了這項變更的認知以外，沒有任何特定的內容。 這種變更只會影響使用 "C" 地區設定對應的應用程式。

### <a name="category"></a>Category

全球化 

### <a name="affected-apis"></a>受影響的 API

所有定序和文化特性 Api 都會受到這項變更的影響。

<!--

-->
