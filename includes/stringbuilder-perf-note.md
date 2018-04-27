在下列狀況下，搭配使用以字元為主的索引與 <xref:System.Text.StringBuilder.Chars%2A> 屬性可能極為緩慢：

- <xref:System.Text.StringBuilder> 執行個體很大 (例如，它包含幾萬個字元)。
- <xref:System.Text.StringBuilder> 是「塊狀」。 也就是說，重複呼叫方法 (例如 <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>) 已自動展開物件的 <xref:System.Text.StringBuilder.Capacity%2A?displayProperty=nameWithType> 屬性並配置記憶體的新區塊給它。

由於每個字元的存取會行經整個連結的區塊清單來尋找要編入索引的正確緩衝區，因此會嚴重影響效能。

> [!NOTE]
>  即使對於大型「塊狀」<xref:System.Text.StringBuilder> 物件，使用 <xref:System.Text.StringBuilder.Chars%2A> 對一個或少數字元進行以索引為主的存取，也只有些許的效能影響；一般來說，這是 **0(n)** 作業。 逐一查看 <xref:System.Text.StringBuilder> 物件中的字元時，就會發生顯著的效能影響，這是 **O(n^2)** 作業。 

如果在 <xref:System.Text.StringBuilder> 物件中使用以字元為主的索引時遇到效能問題，您可以使用下列任一因應措施：

- 藉由呼叫 <xref:System.Text.StringBuilder.ToString%2A> 方法將 <xref:System.Text.StringBuilder> 執行個體轉換為 <xref:System.String>，然後存取字串中的字元。

- 將現有 <xref:System.Text.StringBuilder> 物件的內容複製到預留大小的新 <xref:System.Text.StringBuilder> 物件。 因為新的 <xref:System.Text.StringBuilder> 物件不是塊狀，所以會改善效能。 例如: 

   ```csharp
   // sbOriginal is the existing StringBuilder object
   var sbNew = new StringBuilder(sbOriginal.ToString(), sbOriginal.Length);
   ```
   ```vb
   ' sbOriginal is the existing StringBuilder object
   Dim sbNew = New StringBuilder(sbOriginal.ToString(), sbOriginal.Length)
   ```
- 藉由呼叫 <xref:System.Text.StringBuilder.%23ctor(System.Int32)> 建構函式，將 <xref:System.Text.StringBuilder> 物件的初始容量設定為大約等於其預期大小上限的值。 請注意，即使 <xref:System.Text.StringBuilder> 很少達到其最大容量，這也會配置整個記憶體區塊。
