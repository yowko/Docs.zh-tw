---
title: dateTimeInvalidLocalFormat MDA
ms.date: 03/30/2017
helpviewer_keywords:
- dates [.NET Framework], formatting
- invalid date time local format
- invalid local formats
- MDAs (managed debugging assistants), invalid local formats
- managed debugging assistants (MDAs), invalid local formats
- dateTimeInvalidLocalFormat MDA
- date formatting
- time formatting
- UTC formatting
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 380334dbe9b91ea369de6cbe58686a9a74254c2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874662"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="c8de6-102">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="c8de6-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="c8de6-103">使用只能用於當地 <xref:System.DateTime> 執行個體的格式來格式化儲存為全球定位時間 (UTC) 的 <xref:System.DateTime> 執行個體時，會啟用 `dateTimeInvalidLocalFormat` MDA。</span><span class="sxs-lookup"><span data-stu-id="c8de6-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="c8de6-104">針對未指定或預設 <xref:System.DateTime> 執行個體，不會啟用此 MDA。</span><span class="sxs-lookup"><span data-stu-id="c8de6-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="c8de6-105">徵兆</span><span class="sxs-lookup"><span data-stu-id="c8de6-105">Symptom</span></span>  
 <span data-ttu-id="c8de6-106">應用程式使用當地格式手動序列化 UTC <xref:System.DateTime> 執行個體：</span><span class="sxs-lookup"><span data-stu-id="c8de6-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="c8de6-107">原因</span><span class="sxs-lookup"><span data-stu-id="c8de6-107">Cause</span></span>  
 <span data-ttu-id="c8de6-108"><xref:System.DateTime.ToString%2A?displayProperty=nameWithType> 方法的 'z' 格式包含當地時區位移，例如，"+10:00" 表示雪梨時間。</span><span class="sxs-lookup"><span data-stu-id="c8de6-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="c8de6-109">因此，如果 <xref:System.DateTime> 的值是當地時間，則它只會產生有意義的結果。</span><span class="sxs-lookup"><span data-stu-id="c8de6-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="c8de6-110">如果值是 UTC 時間，則 <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> 會包含當地時區位移，但不會顯示或調整時區規範。</span><span class="sxs-lookup"><span data-stu-id="c8de6-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="c8de6-111">解決方式</span><span class="sxs-lookup"><span data-stu-id="c8de6-111">Resolution</span></span>  
 <span data-ttu-id="c8de6-112">UTC <xref:System.DateTime> 執行個體應該使用指出它們為 UTC 的方式進行格式化。</span><span class="sxs-lookup"><span data-stu-id="c8de6-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="c8de6-113">UTC 時間的建議格式是使用 'Z' 表示 UTC 時間：</span><span class="sxs-lookup"><span data-stu-id="c8de6-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="c8de6-114">也有 "o" 格式可序列化利用正確序列化之 <xref:System.DateTime.Kind%2A> 屬性的 <xref:System.DateTime>，不論執行個體是當地時間、UTC 還是未指定都一樣：</span><span class="sxs-lookup"><span data-stu-id="c8de6-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c8de6-115">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="c8de6-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="c8de6-116">此 MDA 不會影響執行階段。</span><span class="sxs-lookup"><span data-stu-id="c8de6-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c8de6-117">Output</span><span class="sxs-lookup"><span data-stu-id="c8de6-117">Output</span></span>  
 <span data-ttu-id="c8de6-118">此 MDA 啟用沒有任何特殊輸出。不過，呼叫堆疊可以用來決定已啟用 MDA 之 <xref:System.DateTime.ToString%2A> 呼叫的位置。</span><span class="sxs-lookup"><span data-stu-id="c8de6-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c8de6-119">組態</span><span class="sxs-lookup"><span data-stu-id="c8de6-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="c8de6-120">範例</span><span class="sxs-lookup"><span data-stu-id="c8de6-120">Example</span></span>  
 <span data-ttu-id="c8de6-121">請以下列方式考慮使用利用 <xref:System.Xml.XmlConvert> 或 <xref:System.Data.DataSet> 類別間接序列化 UTC <xref:System.DateTime> 值的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c8de6-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="c8de6-122"><xref:System.Xml.XmlConvert> 和 <xref:System.Data.DataSet> 序列化預設會使用當地格式進行序列化。</span><span class="sxs-lookup"><span data-stu-id="c8de6-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="c8de6-123">需要其他選項，才能序列化其他類型的 <xref:System.DateTime> 值，例如 UTC。</span><span class="sxs-lookup"><span data-stu-id="c8de6-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="c8de6-124">在此特定範例中，將 `XmlDateTimeSerializationMode.RoundtripKind` 傳入 `XmlConvert` 上的 `ToString` 呼叫。</span><span class="sxs-lookup"><span data-stu-id="c8de6-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="c8de6-125">這會將資料序列化為 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="c8de6-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="c8de6-126">如果使用 <xref:System.Data.DataSet>，請將 <xref:System.Data.DataColumn> 物件上的 <xref:System.Data.DataColumn.DateTimeMode%2A> 屬性設定為 <xref:System.Data.DataSetDateTime.Utc>。</span><span class="sxs-lookup"><span data-stu-id="c8de6-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8de6-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8de6-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="c8de6-128">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="c8de6-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
