---
title: "如何：讓使用者解決不明確的時間"
description: "如何讓使用者解決不明確的時間"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d6858a5c-02ab-4367-9e08-fa22c051c38d
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: ede8d021a4f524cf37f7ad00b6aed89d1b1729f8
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="7339e-104">如何：讓使用者解決不明確的時間</span><span class="sxs-lookup"><span data-stu-id="7339e-104">How to: let users resolve ambiguous times</span></span>

<span data-ttu-id="7339e-105">不明確的時間是指對應到多個國際標準時間 (UTC) 的時間。</span><span class="sxs-lookup"><span data-stu-id="7339e-105">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="7339e-106">發生時機是往回調整時鐘時間，例如從時區的日光節約時間轉換到其標準時間期間。</span><span class="sxs-lookup"><span data-stu-id="7339e-106">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="7339e-107">處理不明確的時間時，您可以執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="7339e-107">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="7339e-108">如果不明確的時間是使用者所輸入的資料項目，可交由使用者解決此不明確狀況。</span><span class="sxs-lookup"><span data-stu-id="7339e-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

* <span data-ttu-id="7339e-109">假設如何將時間對應至 UTC。</span><span class="sxs-lookup"><span data-stu-id="7339e-109">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="7339e-110">例如，您可以假設不明確的時間一律是以時區的標準時間表示。</span><span class="sxs-lookup"><span data-stu-id="7339e-110">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="7339e-111">本文示範如何讓使用者解決不明確的時間。</span><span class="sxs-lookup"><span data-stu-id="7339e-111">This article shows how to let a user resolve an ambiguous time.</span></span>

## <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="7339e-112">讓使用者解決不明確的時間</span><span class="sxs-lookup"><span data-stu-id="7339e-112">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="7339e-113">取得使用者的時間和日期輸入。</span><span class="sxs-lookup"><span data-stu-id="7339e-113">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="7339e-114">呼叫 [IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) 或 [IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) 方法，以判斷時間是否不明確。</span><span class="sxs-lookup"><span data-stu-id="7339e-114">Call the [IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) or [IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="7339e-115">讓使用者選取想要的位移。</span><span class="sxs-lookup"><span data-stu-id="7339e-115">Let the user select the desired offset.</span></span>

4. <span data-ttu-id="7339e-116">將當地時間減去使用者所選取的位移，以取得 UTC 日期和時間。</span><span class="sxs-lookup"><span data-stu-id="7339e-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

5. <span data-ttu-id="7339e-117">呼叫 `static` (在 Visual Basic 中為 `Shared`) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) 方法，以將 UTC 日期和時間值的 [Kind](xref:System.DateTime.Kind) 屬性設定為 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc)。</span><span class="sxs-lookup"><span data-stu-id="7339e-117">Call the `static` (`Shared` in Visual Basic ) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method to set the UTC date and time value's [Kind](xref:System.DateTime.Kind) property to [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

## <a name="example"></a><span data-ttu-id="7339e-118">範例</span><span class="sxs-lookup"><span data-stu-id="7339e-118">Example</span></span>

<span data-ttu-id="7339e-119">下列範例會提示使用者輸入日期和時間，若其不明確，可讓使用者選取不明確時間所對應的 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="7339e-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span> <span data-ttu-id="7339e-120">本範例使用 [DateTime](xref:System.DateTime) 物件；您可以在需要時取代 [DateTimeOffset](xref:System.DateTimeOffset) 物件。</span><span class="sxs-lookup"><span data-stu-id="7339e-120">The example uses a [DateTime](xref:System.DateTime) object; you can substitute a [DateTimeOffset](xref:System.DateTimeOffset) object if desired.</span></span>

```csharp
private void GetUserDateInput()
{
   // Get date and time from user
   DateTime inputDate = GetUserDateTime();
   DateTime utcDate;

   // Exit if date has no significant value
   if (inputDate == DateTime.MinValue) return;

   if (TimeZoneInfo.Local.IsAmbiguousTime(inputDate))
   {
      Console.WriteLine("The date you've entered is ambiguous.");
      Console.WriteLine("Please select the correct offset from Universal Coordinated Time:");
      TimeSpan[] offsets = TimeZoneInfo.Local.GetAmbiguousTimeOffsets(inputDate);
      for (int ctr = 0; ctr < offsets.Length; ctr++)
      {
         Console.WriteLine("{0}.) {1} hours, {2} minutes", ctr, offsets[ctr].Hours, offsets[ctr].Minutes);
      }
      Console.Write("> ");
      int selection = Convert.ToInt32(Console.ReadLine());

      // Convert local time to UTC, and set Kind property to DateTimeKind.Utc
      utcDate = DateTime.SpecifyKind(inputDate - offsets[selection], DateTimeKind.Utc);

      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString());
   }
   else
   {
      utcDate = inputDate.ToUniversalTime();
      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString());    
   }
}

private DateTime GetUserDateTime() 
{
   bool exitFlag = false;             // flag to exit loop if date is valid
   string dateString;  
   DateTime inputDate = DateTime.MinValue;

   Console.Write("Enter a local date and time: ");
   while (! exitFlag)
   {
      dateString = Console.ReadLine();
      if (dateString.ToUpper() == "E")
         exitFlag = true;

      if (DateTime.TryParse(dateString, out inputDate))
         exitFlag = true;
      else
         Console.Write("Enter a valid date and time, or enter 'e' to exit: ");
   }

   return inputDate;        
}
```

```vb
Private Sub GetUserDateInput()
   ' Get date and time from user
   Dim inputDate As Date = GetUserDateTime()
   Dim utcDate As Date

   ' Exit if date has no significant value
   If inputDate = Date.MinValue Then Exit Sub

   If TimeZoneInfo.Local.IsAmbiguousTime(inputDate) Then
      Console.WriteLine("The date you've entered is ambiguous.")
      Console.WriteLine("Please select the correct offset from Universal Coordinated Time:")
      Dim offsets() As TimeSpan = TimeZoneInfo.Local.GetAmbiguousTimeOffsets(inputDate)
      For ctr As Integer = 0 to offsets.Length - 1
         Dim zoneDescription As String
         If offsets(ctr).Equals(TimeZoneInfo.Local.BaseUtcOffset) Then 
            zoneDescription = TimeZoneInfo.Local.StandardName
         Else
            zoneDescription = TimeZoneInfo.Local.DaylightName
         End If
         Console.WriteLine("{0}.) {1} hours, {2} minutes ({3})", _
                           ctr, offsets(ctr).Hours, offsets(ctr).Minutes, zoneDescription)
      Next         
      Console.Write("> ")
      Dim selection As Integer = CInt(Console.ReadLine())

      ' Convert local time to UTC, and set Kind property to DateTimeKind.Utc
      utcDate = Date.SpecifyKind(inputDate - offsets(selection), DateTimeKind.Utc)

      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString())
   Else
      utcDate = inputDate.ToUniversalTime()
      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString())    
   End If
End Sub

Private Function GetUserDateTime() As Date
   Dim exitFlag As Boolean = False            ' flag to exit loop if date is valid
   Dim dateString As String 
   Dim inputDate As Date = Date.MinValue

   Console.Write("Enter a local date and time: ")
   Do While Not exitFlag
      dateString = Console.ReadLine()
      If dateString.ToUpper = "E" Then exitFlag = True
      If Date.TryParse(dateString, inputDate) Then
         exitFlag = true
      Else   
         Console.Write("Enter a valid date and time, or enter 'e' to exit: ")
      End If
   Loop

   Return inputDate        
End Function
```

<span data-ttu-id="7339e-121">範例程式碼的核心使用 [TimeSpan](xref:System.TimeSpan) 物件陣列表示不明確時間與 UTC 的可能位移。</span><span class="sxs-lookup"><span data-stu-id="7339e-121">The core of the example code uses an array of [TimeSpan](xref:System.TimeSpan) objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="7339e-122">不過，這些位移不可能對使用者具有任何意義。</span><span class="sxs-lookup"><span data-stu-id="7339e-122">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="7339e-123">若要釐清位移的意義，程式碼也會註明位移是否代表當地時區的標準時間或其日光節約時間。</span><span class="sxs-lookup"><span data-stu-id="7339e-123">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="7339e-124">程式碼會比較位移與 [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) 屬性值，來判斷哪一個是標準時間以及哪一個是日光節約時間。</span><span class="sxs-lookup"><span data-stu-id="7339e-124">The code determines which time is standard and which time is daylight by comparing the offset with the value of the [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property.</span></span> <span data-ttu-id="7339e-125">這個屬性指出 UTC 與時區標準時間的差異。</span><span class="sxs-lookup"><span data-stu-id="7339e-125">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="7339e-126">在此範例中，透過 [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) 屬性進行當地時區的所有參考；當地時區絕不會指派給物件變數。</span><span class="sxs-lookup"><span data-stu-id="7339e-126">In this example, all references to the local time zone are made through the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="7339e-127">這是建議作法，原因是另一個呼叫可能會清除快取的資料，並讓任何指派當地時區的物件失效。</span><span class="sxs-lookup"><span data-stu-id="7339e-127">This is a recommended practice because another call could clear the cached data and invalidate any objects that the local time zone is assigned to.</span></span>

## <a name="see-also"></a><span data-ttu-id="7339e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7339e-128">See Also</span></span>

[<span data-ttu-id="7339e-129">日期、時間及時區</span><span class="sxs-lookup"><span data-stu-id="7339e-129">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="7339e-130">如何：解決不明確的時間</span><span class="sxs-lookup"><span data-stu-id="7339e-130">How to: resolve ambiguous times</span></span>](resolve-ambiguous-times.md)


