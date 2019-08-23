---
title: 常值 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: 6196c1b026b49847bd06cc9cda5ea6b6af289858
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953293"
---
# <a name="literals-entity-sql"></a><span data-ttu-id="76ec2-102">常值 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="76ec2-102">Literals (Entity SQL)</span></span>
<span data-ttu-id="76ec2-103">本主題將描述常值 (Literal) 的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援。</span><span class="sxs-lookup"><span data-stu-id="76ec2-103">This topic describes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] support for literals.</span></span>  
  
## <a name="null"></a><span data-ttu-id="76ec2-104">Null</span><span class="sxs-lookup"><span data-stu-id="76ec2-104">Null</span></span>  
 <span data-ttu-id="76ec2-105">Null 常值是用來代表任何型別的 null 值。</span><span class="sxs-lookup"><span data-stu-id="76ec2-105">The null literal is used to represent the value null for any type.</span></span> <span data-ttu-id="76ec2-106">Null 常值與任何型別都相容。</span><span class="sxs-lookup"><span data-stu-id="76ec2-106">A null literal is compatible with any type.</span></span>  
  
 <span data-ttu-id="76ec2-107">您可以透過 null 常值的轉換作業建立 null 型別。</span><span class="sxs-lookup"><span data-stu-id="76ec2-107">Typed nulls can be created by a cast over a null literal.</span></span> <span data-ttu-id="76ec2-108">如需詳細資訊, 請參閱[CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="76ec2-108">For more information, see [CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md).</span></span>  
  
 <span data-ttu-id="76ec2-109">如需可用的浮動 null 常值可以使用的規則, 請參閱[Null 常值和型別推斷](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="76ec2-109">For rules about where free floating null literals can be used, see [Null Literals and Type Inference](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md).</span></span>  
  
## <a name="boolean"></a><span data-ttu-id="76ec2-110">Boolean</span><span class="sxs-lookup"><span data-stu-id="76ec2-110">Boolean</span></span>  
 <span data-ttu-id="76ec2-111">布林常值是由 `true` 和 `false` 關鍵字代表。</span><span class="sxs-lookup"><span data-stu-id="76ec2-111">Boolean literals are represented by the keywords `true` and `false`.</span></span>  
  
## <a name="integer"></a><span data-ttu-id="76ec2-112">整數</span><span class="sxs-lookup"><span data-stu-id="76ec2-112">Integer</span></span>  
 <span data-ttu-id="76ec2-113">整數常值可以屬於 <xref:System.Int32> 或 <xref:System.Int64> 型別。</span><span class="sxs-lookup"><span data-stu-id="76ec2-113">Integer literals can be of type <xref:System.Int32> or <xref:System.Int64>.</span></span> <span data-ttu-id="76ec2-114"><xref:System.Int32> 常值是一連串數字字元。</span><span class="sxs-lookup"><span data-stu-id="76ec2-114">An <xref:System.Int32> literal is a series of numeric characters.</span></span> <span data-ttu-id="76ec2-115"><xref:System.Int64> 常值是一連串數字字元，後面接著大寫 L。</span><span class="sxs-lookup"><span data-stu-id="76ec2-115">An <xref:System.Int64> literal is series of numeric characters followed by an uppercase L.</span></span>  
  
## <a name="decimal"></a><span data-ttu-id="76ec2-116">Decimal</span><span class="sxs-lookup"><span data-stu-id="76ec2-116">Decimal</span></span>  
 <span data-ttu-id="76ec2-117">固定點數 (十進位) 是一連串數字字元、一個點 (.) 和另一連串數字字元，後面接著大寫的「M」。</span><span class="sxs-lookup"><span data-stu-id="76ec2-117">A fixed-point number (decimal) is a series of numeric characters, a dot (.) and another series of numeric characters followed by an uppercase "M".</span></span>  
  
## <a name="float-double"></a><span data-ttu-id="76ec2-118">單精確度浮點數、雙精確度浮點數</span><span class="sxs-lookup"><span data-stu-id="76ec2-118">Float, Double</span></span>  
 <span data-ttu-id="76ec2-119">雙精確度浮點數是一連串數字字元、小數點 (.) 和另一串數字字元，後面可能接著指數。</span><span class="sxs-lookup"><span data-stu-id="76ec2-119">A double-precision floating point number is a series of numeric characters, a dot (.) and another series of numeric characters possibly followed by an exponent.</span></span> <span data-ttu-id="76ec2-120">單精確度浮點數 (或浮點數 (Float)) 是雙精確度浮點數語法，後面接著小寫 f。</span><span class="sxs-lookup"><span data-stu-id="76ec2-120">A single-precisions floating point number (or float) is a double-precision floating point number syntax followed by the lowercase f.</span></span>  
  
## <a name="string"></a><span data-ttu-id="76ec2-121">String</span><span class="sxs-lookup"><span data-stu-id="76ec2-121">String</span></span>  
 <span data-ttu-id="76ec2-122">字串是以引號括住的一連串字元。</span><span class="sxs-lookup"><span data-stu-id="76ec2-122">A string is a series of characters enclosed in quote marks.</span></span> <span data-ttu-id="76ec2-123">引號可以是兩個單引號 (`'`) 或兩個雙引號 (")。</span><span class="sxs-lookup"><span data-stu-id="76ec2-123">Quotes can be either both single-quotes (`'`) or both double-quotes (").</span></span> <span data-ttu-id="76ec2-124">字元字串常值可以是 Unicode 或非 Unicode。</span><span class="sxs-lookup"><span data-stu-id="76ec2-124">Character string literals can be either Unicode or non-Unicode.</span></span> <span data-ttu-id="76ec2-125">如果要將字元字串常值宣告為 Unicode，請在此常值將會加上一個大寫的 "N"。</span><span class="sxs-lookup"><span data-stu-id="76ec2-125">To declare a character string literal as Unicode, prefix the literal with an uppercase "N".</span></span> <span data-ttu-id="76ec2-126">預設值為非 Unicode 字元字串常值。</span><span class="sxs-lookup"><span data-stu-id="76ec2-126">The default is non-Unicode character string literals.</span></span> <span data-ttu-id="76ec2-127">在 N 和此字串常值裝載之間可以不空格，但 N 必須是大寫。</span><span class="sxs-lookup"><span data-stu-id="76ec2-127">There can be no spaces between the N and the string literal payload, and the N must be uppercase.</span></span>  
  
```  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a><span data-ttu-id="76ec2-128">DateTime</span><span class="sxs-lookup"><span data-stu-id="76ec2-128">DateTime</span></span>  
 <span data-ttu-id="76ec2-129">日期時間常值與地區設定 (Locale) 無關，而且它是由日期部分和時間部分所組成。</span><span class="sxs-lookup"><span data-stu-id="76ec2-129">A datetime literal is independent of locale and is composed of a date part and a time part.</span></span> <span data-ttu-id="76ec2-130">日期和時間部分都是強制的，而且沒有任何預設值。</span><span class="sxs-lookup"><span data-stu-id="76ec2-130">Both date and time parts are mandatory and there are no default values.</span></span>  
  
 <span data-ttu-id="76ec2-131">日期`YYYY`部分必須具有下列格式: - - `MM` `DD` `MM` , 其中是`YYYY`介於0001到9999之間的四位數年份值, 而是介於1到12之間的月份, 而是`DD`對給定月份`MM`有效的日期值。</span><span class="sxs-lookup"><span data-stu-id="76ec2-131">The date part must have the format: `YYYY`-`MM`-`DD`, where `YYYY` is a four digit year value between 0001 and 9999, `MM` is the month between 1 and 12 and `DD` is the day value that is valid for the given month `MM`.</span></span>  
  
 <span data-ttu-id="76ec2-132">時間部分的格式必須是 `HH`:`MM`[:`SS`[.fffffff]]，其中 `HH`是小時值，介於 0 到 23 之間、`MM`是分鐘值，介於 0 到 59 之間、`SS`是秒鐘值，介於 0 到 59 之間，而 fffffff 則是秒鐘的小數部分，值介於 0 到 9999999 之間。</span><span class="sxs-lookup"><span data-stu-id="76ec2-132">The time part must have the format: `HH`:`MM`[:`SS`[.fffffff]], where `HH` is the hour value between 0 and 23, `MM` is the minute value between 0 and 59, `SS` is the second value between 0 and 59 and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="76ec2-133">以上所有值的範圍都包含在內。</span><span class="sxs-lookup"><span data-stu-id="76ec2-133">All value ranges are inclusive.</span></span> <span data-ttu-id="76ec2-134">秒鐘的小數部分則為選擇性。</span><span class="sxs-lookup"><span data-stu-id="76ec2-134">Fractional seconds are optional.</span></span> <span data-ttu-id="76ec2-135">除非已指定秒鐘的小數部分，否則秒鐘亦為選擇性；但指定秒鐘的小數部分時，則必須有秒鐘。</span><span class="sxs-lookup"><span data-stu-id="76ec2-135">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="76ec2-136">如果未指定秒鐘或秒鐘的小數部分，則會使用預設值 0。</span><span class="sxs-lookup"><span data-stu-id="76ec2-136">When seconds or fractional seconds are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="76ec2-137">DATETIME 符號與常值裝載之間可以有任何數目的空格，但是不能有新行。</span><span class="sxs-lookup"><span data-stu-id="76ec2-137">There can be any number of spaces between the DATETIME symbol and the literal payload, but no new lines.</span></span>  
  
```  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a><span data-ttu-id="76ec2-138">時間</span><span class="sxs-lookup"><span data-stu-id="76ec2-138">Time</span></span>  
 <span data-ttu-id="76ec2-139">時間常值會依地區設定而異，而且僅由時間部分組成。</span><span class="sxs-lookup"><span data-stu-id="76ec2-139">A time literal is independent of locale and composed of a time part only.</span></span> <span data-ttu-id="76ec2-140">時間部分為必要項，而且沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="76ec2-140">The time part is mandatory and there is no default value.</span></span> <span data-ttu-id="76ec2-141">它必須是 HH:MM[:SS[.fffffff]] 格式，其中 HH 是小時，值介於 0 到 23 之間；MM 是分鐘，值介於 0 到 59 之間；SS 是秒鐘，值介於 0 到 59 之間；而 fffffff 則是秒鐘的小數部分，值介於 0 到 9999999 之間。</span><span class="sxs-lookup"><span data-stu-id="76ec2-141">It must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the second fraction value between 0 and 9999999.</span></span> <span data-ttu-id="76ec2-142">以上所有值的範圍都包含在內。</span><span class="sxs-lookup"><span data-stu-id="76ec2-142">All value ranges are inclusive.</span></span> <span data-ttu-id="76ec2-143">秒鐘的小數部分則為選擇性。</span><span class="sxs-lookup"><span data-stu-id="76ec2-143">Fractional seconds are optional.</span></span> <span data-ttu-id="76ec2-144">除非已指定秒鐘的小數部分，否則秒鐘亦為選擇性；但指定秒鐘的小數部分時，則必須有秒鐘。</span><span class="sxs-lookup"><span data-stu-id="76ec2-144">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="76ec2-145">如果未指定秒鐘或秒鐘的小數部分，則會使用預設值 0。</span><span class="sxs-lookup"><span data-stu-id="76ec2-145">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="76ec2-146">TIME 符號與常值裝載之間可以有任何數目的空格，但是不能有新行。</span><span class="sxs-lookup"><span data-stu-id="76ec2-146">There can be any number of spaces between the TIME symbol and the literal payload, but no new lines.</span></span>  
  
```  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a><span data-ttu-id="76ec2-147">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="76ec2-147">DateTimeOffset</span></span>  
 <span data-ttu-id="76ec2-148">datetimeoffset 常值會依地區設定而異，而且是由日期部分、時間部分和時差部分組成。</span><span class="sxs-lookup"><span data-stu-id="76ec2-148">A datetimeoffset literal is independent of locale and composed of a date part, a time part, and an offset part.</span></span> <span data-ttu-id="76ec2-149">所有日期、時間和時差部分都是必要項，而且沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="76ec2-149">All date, time, and offset parts are mandatory and there are no default values.</span></span> <span data-ttu-id="76ec2-150">日期部分必須是 YYYY-MM-DD 格式，其中 YYYY 是四位數字的年份，值介於 0001 到 9999 之間；MM 是月份，值介於 1 到 12 之間；而 DD 則是所指定月份中的有效日數。</span><span class="sxs-lookup"><span data-stu-id="76ec2-150">The date part must have the format YYYY-MM-DD, where YYYY is a four digit year value between 0001 and 9999, MM is the month between 1 and 12, and DD is the day value that is valid for the given month.</span></span> <span data-ttu-id="76ec2-151">時間部分必須是 HH:MM[:SS[.fffffff]] 格式，其中 HH 是小時，值介於 0 到 23 之間；MM 是分鐘，值介於 0 到 59 之間；SS 是秒鐘，值介於 0 到 59 之間；而 fffffff 則是秒鐘的小數部分，值介於 0 到 9999999 之間。</span><span class="sxs-lookup"><span data-stu-id="76ec2-151">The time part must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="76ec2-152">以上所有值的範圍都包含在內。</span><span class="sxs-lookup"><span data-stu-id="76ec2-152">All value ranges are inclusive.</span></span> <span data-ttu-id="76ec2-153">秒鐘的小數部分則為選擇性。</span><span class="sxs-lookup"><span data-stu-id="76ec2-153">Fractional seconds are optional.</span></span> <span data-ttu-id="76ec2-154">除非已指定秒鐘的小數部分，否則秒鐘亦為選擇性；但指定秒鐘的小數部分時，則必須有秒鐘。</span><span class="sxs-lookup"><span data-stu-id="76ec2-154">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="76ec2-155">如果未指定秒鐘或秒鐘的小數部分，則會使用預設值 0。</span><span class="sxs-lookup"><span data-stu-id="76ec2-155">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span> <span data-ttu-id="76ec2-156">Offset 部分的格式必須是 {+&#124;-} HH: MM, 其中 HH 和 MM 的意義與時間部分相同。</span><span class="sxs-lookup"><span data-stu-id="76ec2-156">The offset part must have the format {+&#124;-}HH:MM, where HH and MM have the same meaning as in the time part.</span></span> <span data-ttu-id="76ec2-157">不過時差的範圍必須介於 -14:00 到 + 14:00 之間</span><span class="sxs-lookup"><span data-stu-id="76ec2-157">The range of the offset, however, must be between -14:00 and + 14:00</span></span>  
  
 <span data-ttu-id="76ec2-158">DATETIMEOFFSET 符號與常值裝載之間可以有任何數目的空格，但是不能有新行。</span><span class="sxs-lookup"><span data-stu-id="76ec2-158">There can be any number of spaces between the DATETIMEOFFSET symbol and the literal payload, but no new lines.</span></span>  
  
```  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> <span data-ttu-id="76ec2-159">有效的 Entity SQL 常值可能會落在 CLR 或資料來源支援的範圍之外。</span><span class="sxs-lookup"><span data-stu-id="76ec2-159">A valid Entity SQL literal value can fall outside the supported ranges for CLR or the data source.</span></span> <span data-ttu-id="76ec2-160">這種情況可能會造成例外狀況</span><span class="sxs-lookup"><span data-stu-id="76ec2-160">This might result in an exception</span></span>  
  
## <a name="binary"></a><span data-ttu-id="76ec2-161">二元</span><span class="sxs-lookup"><span data-stu-id="76ec2-161">Binary</span></span>  
 <span data-ttu-id="76ec2-162">二進位字串常值是以單引號分隔的一連串十六進位數字，後面跟著關鍵字 binary 或捷徑符號 `X` 或 `x`。</span><span class="sxs-lookup"><span data-stu-id="76ec2-162">A binary string literal is a sequence of hexadecimal digits delimited by single quotes following the keyword binary or the shortcut symbol `X` or `x`.</span></span> <span data-ttu-id="76ec2-163">捷徑符號 `X` 不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="76ec2-163">The shortcut symbol `X` is case insensitive.</span></span> <span data-ttu-id="76ec2-164">關鍵字 `binary` 與二進位字串值之間允許使用零個或多個空格。</span><span class="sxs-lookup"><span data-stu-id="76ec2-164">A zero or more spaces are allowed between the keyword `binary` and the binary string value.</span></span>  
  
 <span data-ttu-id="76ec2-165">十六進位字元也不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="76ec2-165">Hexadecimal characters are also case insensitive.</span></span> <span data-ttu-id="76ec2-166">如果此常值所包含的十六進位數是奇數，系統就會在常值前面加上一個十六進位零位數，讓此常值與下一個偶數的十六進位數對齊。</span><span class="sxs-lookup"><span data-stu-id="76ec2-166">If the literal is composed of an odd number of hexadecimal digits, the literal will be aligned to the next even hexadecimal digit by prefixing the literal with a hexadecimal zero digit.</span></span> <span data-ttu-id="76ec2-167">二進位字串的大小沒有正式的限制。</span><span class="sxs-lookup"><span data-stu-id="76ec2-167">There is no formal limit on the size of the binary string.</span></span>  
  
```  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a><span data-ttu-id="76ec2-168">Guid</span><span class="sxs-lookup"><span data-stu-id="76ec2-168">Guid</span></span>  
 <span data-ttu-id="76ec2-169">`GUID` 常值代表全域唯一的識別碼。</span><span class="sxs-lookup"><span data-stu-id="76ec2-169">A `GUID` literal represents a globally unique identifier.</span></span> <span data-ttu-id="76ec2-170">這是由關鍵字`GUID`所組成的序列, 後面接著十六進位數位, 格式為:8-4-4-4-12 以單引號括住。</span><span class="sxs-lookup"><span data-stu-id="76ec2-170">It is a sequence formed by the keyword `GUID` followed by hexadecimal digits in the form known as *registry* format: 8-4-4-4-12 enclosed in single quotes.</span></span> <span data-ttu-id="76ec2-171">十六進位數不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="76ec2-171">Hexadecimal digits are case insensitive.</span></span>  
  
 <span data-ttu-id="76ec2-172">GUID 符號與常值裝載之間可以有任何數目的空格，但是不能有新行。</span><span class="sxs-lookup"><span data-stu-id="76ec2-172">There can be any number of spaces between the GUID symbol and the literal payload, but no new lines.</span></span>  
  
```  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a><span data-ttu-id="76ec2-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76ec2-173">See also</span></span>

- [<span data-ttu-id="76ec2-174">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="76ec2-174">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
