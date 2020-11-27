---
ms.openlocfilehash: c0551fa086644497c631cd9b6d7058398ff9ccfa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702269"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>"C" 地區設定對應至不變的地區設定

.NET Core 2.2 及更早版本相依于預設的 ICU 行為，此行為會將 "C" 地區設定對應至 en_US_POSIX 地區設定。 En_US_POSIX 地區設定有不必要的定序行為，因為它不支援不區分大小寫的字串比較。 因為某些 Linux 發行版本會將 "C" 地區設定設定為預設地區設定，所以使用者會遇到非預期的行為。

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0 開始，"C" 地區設定對應已變更為使用不變的地區設定，而不是 en_US_POSIX。 「非變異」對應的 "C" 地區設定也適用于 Windows，以保持一致性。

將 "C" 對應至 en_US_POSIX 文化特性會造成客戶的混淆，因為 en_US_POSIX 不支援不區分大小寫的排序/搜尋字串作業。 因為 "C" 地區設定在某些 Linux 散發版本中是用來做為預設的地區設定，所以客戶在這些作業系統上遇到這類不想要的行為。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

這項變更不會有任何特定的功能。 這種變更只會影響使用 "C" 地區設定對應的應用程式。

#### <a name="category"></a>類別

全球化

#### <a name="affected-apis"></a>受影響的 API

所有定序和文化特性 Api 都會受到這項變更的影響。

<!--

#### Affected APIs

-->
