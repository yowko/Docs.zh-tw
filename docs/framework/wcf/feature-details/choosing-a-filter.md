---
title: 選擇篩選
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 908e905b4196409b00abccccae03436640cbe986
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045982"
---
# <a name="choosing-a-filter"></a>選擇篩選
設定路由服務時，務必選取正確的訊息篩選條件，並將它們設定為可針對您所接收的訊息進行正確的比對。 如果您選取的篩選條件在比對中過度廣泛，或設定不正確，則無法正確傳送訊息。 如果篩選條件過於嚴格，則部分訊息可能會沒有可用的有效路由。

## <a name="filter-types"></a>篩選條件類型

選取由路由服務所使用的篩選條件時，務必了解每個篩選條件的運作方式，以及傳入訊息中有何可用的資訊。 例如，如果所有的訊息都是由相同的端點接收，Address 和 EndpointName 篩選條件的用處便不大，因為所有的訊息都符合這些篩選條件。

### <a name="action"></a>動作

Action 篩選條件會檢查 <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> 屬性。 如果訊息中的 Action 標頭內容符合在篩選組態中指定的篩選資料值，則此篩選條件會傳回 `true`。 下列範例`FilterElement`會定義, 其使用動作篩選準則來比對具有包含值之`http://namespace/contract/operation/`動作標頭的訊息。

```xml
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />
```

```csharp
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
```

當路由訊息包含唯一的動作標頭時，應該使用此篩選條件。

### <a name="endpointaddress"></a>EndpointAddress

EndpointAddress 篩選條件會檢查收到訊息的 EndpointAddress。 如果訊息到達的位址完全符合在篩選組態中指定的篩選位址，則此篩選條件會傳回 `true`。 下列範例`FilterElement`會定義, 其使用位址篩選準則來比對任何定址為 "HTTP://\<hostname >/vdir/s.svc/b" 的訊息。

```xml
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> 請務必注意，位址的主機名稱部分可根據用戶端是否使用完全合格的網域名稱、NetBIOS 名稱、IP 位址或其他名稱，而有所不同。 因為不同的值可代表相同的主機，此項比較的預設行為在執行比對時，不會使用位址的主機名稱部分。
>
> 此行為可加以修改，以便在以程式設計方式設定路由服務時，讓比較評估主機名稱。

當傳入訊息為唯一位址時，應該使用此篩選條件。

### <a name="endpointaddressprefix"></a>EndpointAddressPrefix

EndpointAddressPrefix 篩選條件與 EndpointAddress 篩選條件類似。 EndpointAddressPrefix 篩選條件會檢查收到訊息的 EndpointAddress。 不過，EndpointAddressPrefix 篩選條件會藉由比對以在篩選組態中指定之值開始的位址，以萬元字元的方式呈現。 下列範例`FilterElement`會定義, 其使用 EndpointAddressPrefix 篩選準則來比對任何已定址`http://<hostname>/vdir*`的訊息。

```xml
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />
```

```csharp
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> 請務必注意，位址的主機名稱部分可根據用戶端是否使用完全合格的網域名稱、NetBIOS 名稱、IP 位址或其他名稱，而有所不同。 因為不同的值可代表相同的主機，此項比較的預設行為在執行比對時，不會使用位址的主機名稱部分。

當路由共用通用位址首碼的傳入訊息時，應該使用此篩選條件。

### <a name="and"></a>AND

AND 篩選條件不會直接在訊息的值中篩選，不過可讓您結合兩種其他篩選條件以建立 `AND` 條件，其中兩種篩選條件必須在 AND 篩選條件評估為 `true` 前比對訊息。 這樣做可讓您建立複雜篩選，僅在所有子篩選符合時才比對。 下列範例定義位址篩選和動作篩選，然後定義針對位址和動作篩選評估訊息的 AND 篩選條件。 如果位址和動作篩選符合，則 AND 篩選條件會傳回 `true`。

```xml
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);
```

當您必須從多個篩選條件中結合邏輯，以便決定何時進行比對時，應使用此篩選。 例如，如果您有多個必須接收僅部分動作和特定位址訊息結合的目的地，便可使用 AND 篩選條件來結合必要的 Action 和 Address 篩選條件。

### <a name="custom"></a>自訂

選取自訂篩選類型時, 您必須提供 customType 值, 其中包含包含要用於此篩選之**MessageFilter**執行的元件類型。 另外，filterData 必須包含自訂篩選在其訊息評估中可能需要的任何值。 下列範例會定義 `FilterElement`，其使用 `CustomAssembly.MyCustomMsgFilter` MessageFilter 實作。

```xml
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />
```

```csharp
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");
```

如果您需要針對提供[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]的篩選器未涵蓋的訊息執行自訂比對邏輯, 您必須建立**MessageFilter**類別的實作為自訂篩選。 例如，您可能要建立自訂篩選條件，此篩選條件會針對做為組態之篩選的已知值清單，在傳入訊息中比較欄位；或建立特定訊息項目雜湊，然後檢查該值以決定篩選是否應傳回 `true` 或 `false`。

### <a name="endpointname"></a>EndpointName

EndpointName 篩選條件會檢查已接受到訊息的端點名稱。 下列範例`FilterElement`會定義, 其使用端點篩選準則來路由傳送至 "SvcEndpoint" 的訊息。

```xml
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />
```

```csharp
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");
```

當路由服務公開一個以上的已命名服務端點時，此篩選條件便非常有用。 例如，您可能會公開兩個路由服務用來接收訊息的端點，一個是由有優先權，需要即時處理訊息的客戶所使用，另一個端點則可接收較無時間緊迫性的訊息。

當您可時常使用完整位址比對來決定要接收訊息的端點時，使用定義的端點名稱會是較方便的捷徑，因為較不易有錯誤，尤其是在使用組態檔設定路由服務時 (在組態檔中，端點名稱為必要屬性)。

### <a name="matchall"></a>MatchAll

MatchAll 篩選條件會比對所有收到的訊息。 如果您必須時常傳送所有收到的訊息至特定端點 (例如儲存所有已接收訊息複本的記錄服務) 此篩選條件便非常有用。 下列範例會定義 `FilterElement`，其使用 MatchAll 篩選條件。

```xml
<filter name="matchAll1" filterType="MatchAll" />
```

```csharp
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();
```

### <a name="xpath"></a>XPath

XPath 篩選條件可讓您指定 XPath 查詢，該查詢是用來檢查訊息中的特定項目。 XPath 篩選是相當強大的篩選選項，可讓您直接檢查訊息中的任何 XML 位址項目，不過您必須對所接收之訊息的結構有一定程度的了解。 下列範例`FilterElement`會定義, 其使用 XPath 篩選準則, 在 "ns" 命名空間前置詞所參考的命名空間中, 檢查名為 "element" 之元素的訊息。

```xml
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />
```

```csharp
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");
```

如果您知道正在接收的訊息包含特定值時，此篩選便非常有用。 例如，如果您正在裝載相同服務的兩個不同版本，而且知道傳送到較新服務版本的訊息，在自訂標頭中包含唯一的值，便可建立使用 XPath 的篩選條件來導覽至此標頭，並將出現在標頭中的值與篩選組態中另一個值進行比較，以決定篩選條件是否相符。

由於 XPath 查詢通常包含唯一的命名空間，而該空間通常有冗長或複雜的字串值，因此 XPath 篩選條件可讓您使用命名空間資料表來為您的命名空間定義唯一的前置詞。 如需命名空間資料表的詳細資訊, 請參閱[訊息篩選](../../../../docs/framework/wcf/feature-details/message-filters.md)。

如需設計 XPath 查詢的詳細資訊, 請參閱[Xpath 語法](https://go.microsoft.com/fwlink/?LinkId=164592)。

## <a name="see-also"></a>另請參閱

- [訊息篩選](../../../../docs/framework/wcf/feature-details/message-filters.md)
- [如何：使用篩選](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
