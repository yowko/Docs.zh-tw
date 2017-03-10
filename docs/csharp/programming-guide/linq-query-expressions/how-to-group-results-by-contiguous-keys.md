---
redirect_url: /dotnet/articles/csharp/linq/group-results-by-contiguous-keys
caps.handback.revision: 11
---
# 如何：以連續鍵分組結果 (C# 程式設計手冊)
下列範例顯示如何將元素分組成代表連續索引鍵結果的區塊 \(Chunk\)。  例如，假設指定了下列索引鍵\/值組的序列：  
  
|機碼|值|  
|--------|-------|  
|A|We|  
|A|think|  
|A|that|  
|B|Linq|  
|C|是|  
|A|really|  
|B|cool|  
|B|\!|  
  
 會依下列順序建立下列群組：  
  
1.  We、think、that  
  
2.  Linq  
  
3.  是  
  
4.  really  
  
5.  cool、\!  
  
 方案是以擴充方法來實作，它是安全執行緒 \(Thread\-Safe\) 的方法，而且會以資料流 \(Streaming\) 方式傳回其結果。  換言之，它會隨著在整個來源序列移動而產生其群組。  與 `group` 或 `orderby` 運算子不同的是，在讀取完所有序列之前，它就可以開始將群組傳回呼叫端。  
  
 如原始程式碼註解所述，在逐一查看來源序列時產生每個群組或區塊的複本，便可以達成安全執行緒的目的。  如果來源序列有大量連續項目序列，Common Language Runtime 可能會擲回 <xref:System.OutOfMemoryException>。  
  
## 範例  
 下列範例會顯示擴充方法，也一併顯示使用擴充方法的用戶端程式碼。  
  
 [!code-cs[cscsrefContiguousGroups#1](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/how-to-group-results-by-_1.cs)]  
  
 若要在專案中使用擴充方法，請將 `MyExtensions` 靜態類別複製到新的或現有的原始程式碼檔，並視需要在其所在位置處加入命名空間 \(Namespace\) 的 `using` 指示詞。  
  
## 請參閱  
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Classification of Standard Query Operators by Manner of Execution](../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)