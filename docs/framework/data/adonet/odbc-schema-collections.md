---
title: ODBC 結構描述集合
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43750005"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="2c5cf-102">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="2c5cf-102">ODBC Schema Collections</span></span>
<span data-ttu-id="2c5cf-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 ODBC 驅動程式的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="2c5cf-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="2c5cf-104">Microsoft SQL Server ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="2c5cf-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="2c5cf-105">Microsoft SQL Server ODBC 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="2c5cf-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="2c5cf-106">資料表</span><span class="sxs-lookup"><span data-stu-id="2c5cf-106">Tables</span></span>  
  
-   <span data-ttu-id="2c5cf-107">Indexes</span><span class="sxs-lookup"><span data-stu-id="2c5cf-107">Indexes</span></span>  
  
-   <span data-ttu-id="2c5cf-108">資料行</span><span class="sxs-lookup"><span data-stu-id="2c5cf-108">Columns</span></span>  
  
-   <span data-ttu-id="2c5cf-109">程序</span><span class="sxs-lookup"><span data-stu-id="2c5cf-109">Procedures</span></span>  
  
-   <span data-ttu-id="2c5cf-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2c5cf-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="2c5cf-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2c5cf-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="2c5cf-112">檢視</span><span class="sxs-lookup"><span data-stu-id="2c5cf-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="2c5cf-113">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="2c5cf-113">Tables and Views</span></span>  
  
|<span data-ttu-id="2c5cf-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-114">ColumnName</span></span>|<span data-ttu-id="2c5cf-115">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="2c5cf-116">TABLE_CAT</span></span>|<span data-ttu-id="2c5cf-117">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-117">String</span></span>|  
|<span data-ttu-id="2c5cf-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2c5cf-118">TABLE_SCHEM</span></span>|<span data-ttu-id="2c5cf-119">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-119">String</span></span>|  
|<span data-ttu-id="2c5cf-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-120">TABLE_NAME</span></span>|<span data-ttu-id="2c5cf-121">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-121">String</span></span>|  
|<span data-ttu-id="2c5cf-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-122">TABLE_TYPE</span></span>|<span data-ttu-id="2c5cf-123">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-123">String</span></span>|  
|<span data-ttu-id="2c5cf-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-124">REMARKS</span></span>|<span data-ttu-id="2c5cf-125">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="2c5cf-126">Indexes</span><span class="sxs-lookup"><span data-stu-id="2c5cf-126">Indexes</span></span>  
  
|<span data-ttu-id="2c5cf-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-127">ColumnName</span></span>|<span data-ttu-id="2c5cf-128">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="2c5cf-129">TABLE_CAT</span></span>|<span data-ttu-id="2c5cf-130">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-130">String</span></span>|  
|<span data-ttu-id="2c5cf-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2c5cf-131">TABLE_SCHEM</span></span>|<span data-ttu-id="2c5cf-132">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-132">String</span></span>|  
|<span data-ttu-id="2c5cf-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-133">TABLE_NAME</span></span>|<span data-ttu-id="2c5cf-134">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-134">String</span></span>|  
|<span data-ttu-id="2c5cf-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-135">NON_UNIQUE</span></span>|<span data-ttu-id="2c5cf-136">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-136">Int16</span></span>|  
|<span data-ttu-id="2c5cf-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="2c5cf-138">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-138">String</span></span>|  
|<span data-ttu-id="2c5cf-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-139">INDEX_NAME</span></span>|<span data-ttu-id="2c5cf-140">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-140">String</span></span>|  
|<span data-ttu-id="2c5cf-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-141">TYPE</span></span>|<span data-ttu-id="2c5cf-142">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-142">Int16</span></span>|  
|<span data-ttu-id="2c5cf-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c5cf-144">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-144">Int16</span></span>|  
|<span data-ttu-id="2c5cf-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-145">COLUMN_NAME</span></span>|<span data-ttu-id="2c5cf-146">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-146">String</span></span>|  
|<span data-ttu-id="2c5cf-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="2c5cf-147">ASC_OR_DESC</span></span>|<span data-ttu-id="2c5cf-148">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-148">String</span></span>|  
|<span data-ttu-id="2c5cf-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="2c5cf-149">CARDINATLITY</span></span>|<span data-ttu-id="2c5cf-150">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-150">Int32</span></span>|  
|<span data-ttu-id="2c5cf-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="2c5cf-151">PAGES</span></span>|<span data-ttu-id="2c5cf-152">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-152">Int32</span></span>|  
|<span data-ttu-id="2c5cf-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-153">FILTER_CONDITION</span></span>|<span data-ttu-id="2c5cf-154">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-154">String</span></span>|  
|<span data-ttu-id="2c5cf-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c5cf-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="2c5cf-156">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-156">String</span></span>|  
|<span data-ttu-id="2c5cf-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-158">Byte</span><span class="sxs-lookup"><span data-stu-id="2c5cf-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="2c5cf-159">資料行</span><span class="sxs-lookup"><span data-stu-id="2c5cf-159">Columns</span></span>  
  
|<span data-ttu-id="2c5cf-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-160">ColumnName</span></span>|<span data-ttu-id="2c5cf-161">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="2c5cf-162">TABLE_CAT</span></span>|<span data-ttu-id="2c5cf-163">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-163">String</span></span>|  
|<span data-ttu-id="2c5cf-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2c5cf-164">TABLE_SCHEM</span></span>|<span data-ttu-id="2c5cf-165">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-165">String</span></span>|  
|<span data-ttu-id="2c5cf-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-166">TABLE_NAME</span></span>|<span data-ttu-id="2c5cf-167">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-167">String</span></span>|  
|<span data-ttu-id="2c5cf-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-168">COLUMN_NAME</span></span>|<span data-ttu-id="2c5cf-169">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-169">String</span></span>|  
|<span data-ttu-id="2c5cf-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-170">DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-171">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-171">Int16</span></span>|  
|<span data-ttu-id="2c5cf-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-172">TYPE_NAME</span></span>|<span data-ttu-id="2c5cf-173">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-173">String</span></span>|  
|<span data-ttu-id="2c5cf-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-174">COLUMN_SIZE</span></span>|<span data-ttu-id="2c5cf-175">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-175">Int32</span></span>|  
|<span data-ttu-id="2c5cf-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c5cf-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="2c5cf-177">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-177">Int32</span></span>|  
|<span data-ttu-id="2c5cf-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="2c5cf-179">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-179">Int16</span></span>|  
|<span data-ttu-id="2c5cf-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="2c5cf-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="2c5cf-181">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-181">Int16</span></span>|  
|<span data-ttu-id="2c5cf-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-182">NULLABLE</span></span>|<span data-ttu-id="2c5cf-183">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-183">Int16</span></span>|  
|<span data-ttu-id="2c5cf-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-184">REMARKS</span></span>|<span data-ttu-id="2c5cf-185">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-185">String</span></span>|  
|<span data-ttu-id="2c5cf-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="2c5cf-186">COLUMN_DEF</span></span>|<span data-ttu-id="2c5cf-187">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-187">String</span></span>|  
|<span data-ttu-id="2c5cf-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-189">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-189">Int16</span></span>|  
|<span data-ttu-id="2c5cf-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="2c5cf-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="2c5cf-191">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-191">Int16</span></span>|  
|<span data-ttu-id="2c5cf-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c5cf-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="2c5cf-193">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-193">Int32</span></span>|  
|<span data-ttu-id="2c5cf-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c5cf-195">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-195">Int32</span></span>|  
|<span data-ttu-id="2c5cf-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-196">IS_NULLABLE</span></span>|<span data-ttu-id="2c5cf-197">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-197">String</span></span>|  
|<span data-ttu-id="2c5cf-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c5cf-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="2c5cf-199">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-199">String</span></span>|  
|<span data-ttu-id="2c5cf-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c5cf-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="2c5cf-201">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-201">String</span></span>|  
|<span data-ttu-id="2c5cf-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-203">Byte</span><span class="sxs-lookup"><span data-stu-id="2c5cf-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="2c5cf-204">程序</span><span class="sxs-lookup"><span data-stu-id="2c5cf-204">Procedures</span></span>  
  
|<span data-ttu-id="2c5cf-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-205">ColumnName</span></span>|<span data-ttu-id="2c5cf-206">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="2c5cf-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="2c5cf-208">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-208">String</span></span>|  
|<span data-ttu-id="2c5cf-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2c5cf-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="2c5cf-210">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-210">String</span></span>|  
|<span data-ttu-id="2c5cf-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="2c5cf-212">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-212">String</span></span>|  
|<span data-ttu-id="2c5cf-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="2c5cf-214">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-214">Int32</span></span>|  
|<span data-ttu-id="2c5cf-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="2c5cf-216">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-216">Int32</span></span>|  
|<span data-ttu-id="2c5cf-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="2c5cf-218">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-218">Int32</span></span>|  
|<span data-ttu-id="2c5cf-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-219">REMARKS</span></span>|<span data-ttu-id="2c5cf-220">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-220">String</span></span>|  
|<span data-ttu-id="2c5cf-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2c5cf-222">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="2c5cf-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2c5cf-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="2c5cf-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-224">ColumnName</span></span>|<span data-ttu-id="2c5cf-225">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="2c5cf-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="2c5cf-227">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-227">String</span></span>|  
|<span data-ttu-id="2c5cf-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2c5cf-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="2c5cf-229">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-229">String</span></span>|  
|<span data-ttu-id="2c5cf-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="2c5cf-231">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-231">String</span></span>|  
|<span data-ttu-id="2c5cf-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-232">COLUMN_NAME</span></span>|<span data-ttu-id="2c5cf-233">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-233">String</span></span>|  
|<span data-ttu-id="2c5cf-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-234">COLUMN_TYPE</span></span>|<span data-ttu-id="2c5cf-235">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-235">Int16</span></span>|  
|<span data-ttu-id="2c5cf-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-236">DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-237">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-237">Int16</span></span>|  
|<span data-ttu-id="2c5cf-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-238">TYPE_NAME</span></span>|<span data-ttu-id="2c5cf-239">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-239">String</span></span>|  
|<span data-ttu-id="2c5cf-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-240">COLUMN_SIZE</span></span>|<span data-ttu-id="2c5cf-241">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-241">Int32</span></span>|  
|<span data-ttu-id="2c5cf-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c5cf-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="2c5cf-243">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-243">Int32</span></span>|  
|<span data-ttu-id="2c5cf-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="2c5cf-245">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-245">Int16</span></span>|  
|<span data-ttu-id="2c5cf-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="2c5cf-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="2c5cf-247">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-247">Int16</span></span>|  
|<span data-ttu-id="2c5cf-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-248">NULLABLE</span></span>|<span data-ttu-id="2c5cf-249">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-249">Int16</span></span>|  
|<span data-ttu-id="2c5cf-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-250">REMARKS</span></span>|<span data-ttu-id="2c5cf-251">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-251">String</span></span>|  
|<span data-ttu-id="2c5cf-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="2c5cf-252">COLUMN_DEF</span></span>|<span data-ttu-id="2c5cf-253">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-253">String</span></span>|  
|<span data-ttu-id="2c5cf-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-255">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-255">Int16</span></span>|  
|<span data-ttu-id="2c5cf-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="2c5cf-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="2c5cf-257">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-257">Int16</span></span>|  
|<span data-ttu-id="2c5cf-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c5cf-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="2c5cf-259">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-259">Int32</span></span>|  
|<span data-ttu-id="2c5cf-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c5cf-261">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-261">Int32</span></span>|  
|<span data-ttu-id="2c5cf-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-262">IS_NULLABLE</span></span>|<span data-ttu-id="2c5cf-263">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-263">String</span></span>|  
|<span data-ttu-id="2c5cf-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c5cf-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="2c5cf-265">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-265">String</span></span>|  
|<span data-ttu-id="2c5cf-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c5cf-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="2c5cf-267">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-267">String</span></span>|  
|<span data-ttu-id="2c5cf-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-269">Byte</span><span class="sxs-lookup"><span data-stu-id="2c5cf-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="2c5cf-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2c5cf-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="2c5cf-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-271">ColumnName</span></span>|<span data-ttu-id="2c5cf-272">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="2c5cf-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="2c5cf-274">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-274">String</span></span>|  
|<span data-ttu-id="2c5cf-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2c5cf-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="2c5cf-276">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-276">String</span></span>|  
|<span data-ttu-id="2c5cf-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="2c5cf-278">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-278">String</span></span>|  
|<span data-ttu-id="2c5cf-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-279">COLUMN_NAME</span></span>|<span data-ttu-id="2c5cf-280">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-280">String</span></span>|  
|<span data-ttu-id="2c5cf-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-281">COLUMN_TYPE</span></span>|<span data-ttu-id="2c5cf-282">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-282">Int16</span></span>|  
|<span data-ttu-id="2c5cf-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-283">DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-284">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-284">Int16</span></span>|  
|<span data-ttu-id="2c5cf-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-285">TYPE_NAME</span></span>|<span data-ttu-id="2c5cf-286">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-286">String</span></span>|  
|<span data-ttu-id="2c5cf-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-287">COLUMN_SIZE</span></span>|<span data-ttu-id="2c5cf-288">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-288">Int32</span></span>|  
|<span data-ttu-id="2c5cf-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c5cf-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="2c5cf-290">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-290">Int32</span></span>|  
|<span data-ttu-id="2c5cf-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="2c5cf-292">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-292">Int16</span></span>|  
|<span data-ttu-id="2c5cf-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="2c5cf-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="2c5cf-294">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-294">Int16</span></span>|  
|<span data-ttu-id="2c5cf-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-295">NULLABLE</span></span>|<span data-ttu-id="2c5cf-296">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-296">Int16</span></span>|  
|<span data-ttu-id="2c5cf-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-297">REMARKS</span></span>|<span data-ttu-id="2c5cf-298">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-298">String</span></span>|  
|<span data-ttu-id="2c5cf-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="2c5cf-299">COLUMN_DEF</span></span>|<span data-ttu-id="2c5cf-300">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-300">String</span></span>|  
|<span data-ttu-id="2c5cf-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-302">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-302">Int16</span></span>|  
|<span data-ttu-id="2c5cf-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="2c5cf-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="2c5cf-304">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-304">Int16</span></span>|  
|<span data-ttu-id="2c5cf-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c5cf-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="2c5cf-306">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-306">Int32</span></span>|  
|<span data-ttu-id="2c5cf-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c5cf-308">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-308">Int32</span></span>|  
|<span data-ttu-id="2c5cf-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-309">IS_NULLABLE</span></span>|<span data-ttu-id="2c5cf-310">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-310">String</span></span>|  
|<span data-ttu-id="2c5cf-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c5cf-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="2c5cf-312">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-312">String</span></span>|  
|<span data-ttu-id="2c5cf-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c5cf-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="2c5cf-314">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-314">String</span></span>|  
|<span data-ttu-id="2c5cf-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-316">Byte</span><span class="sxs-lookup"><span data-stu-id="2c5cf-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="2c5cf-317">Microsoft Oracle ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="2c5cf-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="2c5cf-318">Microsoft SQL Server Oracle ODBC 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="2c5cf-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="2c5cf-319">資料表</span><span class="sxs-lookup"><span data-stu-id="2c5cf-319">Tables</span></span>  
  
-   <span data-ttu-id="2c5cf-320">資料行</span><span class="sxs-lookup"><span data-stu-id="2c5cf-320">Columns</span></span>  
  
-   <span data-ttu-id="2c5cf-321">程序</span><span class="sxs-lookup"><span data-stu-id="2c5cf-321">Procedures</span></span>  
  
-   <span data-ttu-id="2c5cf-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2c5cf-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="2c5cf-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2c5cf-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="2c5cf-324">檢視</span><span class="sxs-lookup"><span data-stu-id="2c5cf-324">Views</span></span>  
  
-   <span data-ttu-id="2c5cf-325">Indexes</span><span class="sxs-lookup"><span data-stu-id="2c5cf-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="2c5cf-326">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="2c5cf-326">Tables and Views</span></span>  
  
|<span data-ttu-id="2c5cf-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-327">ColumnName</span></span>|<span data-ttu-id="2c5cf-328">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="2c5cf-330">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-330">String</span></span>|  
|<span data-ttu-id="2c5cf-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-331">TABLE_OWNER</span></span>|<span data-ttu-id="2c5cf-332">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-332">String</span></span>|  
|<span data-ttu-id="2c5cf-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-333">TABLE_NAME</span></span>|<span data-ttu-id="2c5cf-334">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-334">String</span></span>|  
|<span data-ttu-id="2c5cf-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-335">TABLE_TYPE</span></span>|<span data-ttu-id="2c5cf-336">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-336">String</span></span>|  
|<span data-ttu-id="2c5cf-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-337">REMARKS</span></span>|<span data-ttu-id="2c5cf-338">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="2c5cf-339">資料行</span><span class="sxs-lookup"><span data-stu-id="2c5cf-339">Columns</span></span>  
  
|<span data-ttu-id="2c5cf-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-340">ColumnName</span></span>|<span data-ttu-id="2c5cf-341">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="2c5cf-343">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-343">String</span></span>|  
|<span data-ttu-id="2c5cf-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-344">TABLE_OWNER</span></span>|<span data-ttu-id="2c5cf-345">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-345">String</span></span>|  
|<span data-ttu-id="2c5cf-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-346">TABLE_NAME</span></span>|<span data-ttu-id="2c5cf-347">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-347">String</span></span>|  
|<span data-ttu-id="2c5cf-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-348">COLUMN_NAME</span></span>|<span data-ttu-id="2c5cf-349">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-349">String</span></span>|  
|<span data-ttu-id="2c5cf-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-350">DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-351">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-351">Int16</span></span>|  
|<span data-ttu-id="2c5cf-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-352">TYPE_NAME</span></span>|<span data-ttu-id="2c5cf-353">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-353">String</span></span>|  
|<span data-ttu-id="2c5cf-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-354">PRECISION</span></span>|<span data-ttu-id="2c5cf-355">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-355">Int32</span></span>|  
|<span data-ttu-id="2c5cf-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c5cf-356">LENGTH</span></span>|<span data-ttu-id="2c5cf-357">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-357">Int32</span></span>|  
|<span data-ttu-id="2c5cf-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-358">SCALE</span></span>|<span data-ttu-id="2c5cf-359">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-359">Int16</span></span>|  
|<span data-ttu-id="2c5cf-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="2c5cf-360">RADIX</span></span>|<span data-ttu-id="2c5cf-361">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-361">Int16</span></span>|  
|<span data-ttu-id="2c5cf-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-362">NULLABLE</span></span>|<span data-ttu-id="2c5cf-363">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-363">Int16</span></span>|  
|<span data-ttu-id="2c5cf-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-364">REMARKS</span></span>|<span data-ttu-id="2c5cf-365">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-365">String</span></span>|  
|<span data-ttu-id="2c5cf-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c5cf-367">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="2c5cf-368">程序</span><span class="sxs-lookup"><span data-stu-id="2c5cf-368">Procedures</span></span>  
  
|<span data-ttu-id="2c5cf-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-369">ColumnName</span></span>|<span data-ttu-id="2c5cf-370">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="2c5cf-372">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-372">String</span></span>|  
|<span data-ttu-id="2c5cf-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="2c5cf-374">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-374">String</span></span>|  
|<span data-ttu-id="2c5cf-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="2c5cf-376">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-376">String</span></span>|  
|<span data-ttu-id="2c5cf-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="2c5cf-378">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-378">Int16</span></span>|  
|<span data-ttu-id="2c5cf-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="2c5cf-380">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-380">Int16</span></span>|  
|<span data-ttu-id="2c5cf-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="2c5cf-382">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-382">Int16</span></span>|  
|<span data-ttu-id="2c5cf-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-383">REMARKS</span></span>|<span data-ttu-id="2c5cf-384">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-384">String</span></span>|  
|<span data-ttu-id="2c5cf-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2c5cf-386">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="2c5cf-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2c5cf-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="2c5cf-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-388">ColumnName</span></span>|<span data-ttu-id="2c5cf-389">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="2c5cf-391">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-391">String</span></span>|  
|<span data-ttu-id="2c5cf-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="2c5cf-393">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-393">String</span></span>|  
|<span data-ttu-id="2c5cf-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="2c5cf-395">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-395">String</span></span>|  
|<span data-ttu-id="2c5cf-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-396">COLUMN_NAME</span></span>|<span data-ttu-id="2c5cf-397">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-397">String</span></span>|  
|<span data-ttu-id="2c5cf-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-398">COLUMN_TYPE</span></span>|<span data-ttu-id="2c5cf-399">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-399">Int16</span></span>|  
|<span data-ttu-id="2c5cf-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-400">DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-401">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-401">Int16</span></span>|  
|<span data-ttu-id="2c5cf-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-402">TYPE_NAME</span></span>|<span data-ttu-id="2c5cf-403">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-403">String</span></span>|  
|<span data-ttu-id="2c5cf-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-404">PRECISION</span></span>|<span data-ttu-id="2c5cf-405">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-405">Int32</span></span>|  
|<span data-ttu-id="2c5cf-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c5cf-406">LENGTH</span></span>|<span data-ttu-id="2c5cf-407">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-407">Int32</span></span>|  
|<span data-ttu-id="2c5cf-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-408">SCALE</span></span>|<span data-ttu-id="2c5cf-409">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-409">Int16</span></span>|  
|<span data-ttu-id="2c5cf-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="2c5cf-410">RADIX</span></span>|<span data-ttu-id="2c5cf-411">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-411">Int16</span></span>|  
|<span data-ttu-id="2c5cf-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-412">NULLABLE</span></span>|<span data-ttu-id="2c5cf-413">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-413">Int16</span></span>|  
|<span data-ttu-id="2c5cf-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-414">REMARKS</span></span>|<span data-ttu-id="2c5cf-415">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-415">String</span></span>|  
|<span data-ttu-id="2c5cf-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="2c5cf-416">OVERLOAD</span></span>|<span data-ttu-id="2c5cf-417">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-417">Int32</span></span>|  
|<span data-ttu-id="2c5cf-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c5cf-419">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="2c5cf-420">Microsoft Jet ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="2c5cf-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="2c5cf-421">除了通用結構描述集合之外，Microsoft Jet ODBC 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="2c5cf-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="2c5cf-422">資料表</span><span class="sxs-lookup"><span data-stu-id="2c5cf-422">Tables</span></span>  
  
-   <span data-ttu-id="2c5cf-423">Indexes</span><span class="sxs-lookup"><span data-stu-id="2c5cf-423">Indexes</span></span>  
  
-   <span data-ttu-id="2c5cf-424">資料行</span><span class="sxs-lookup"><span data-stu-id="2c5cf-424">Columns</span></span>  
  
-   <span data-ttu-id="2c5cf-425">程序</span><span class="sxs-lookup"><span data-stu-id="2c5cf-425">Procedures</span></span>  
  
-   <span data-ttu-id="2c5cf-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2c5cf-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="2c5cf-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2c5cf-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="2c5cf-428">檢視</span><span class="sxs-lookup"><span data-stu-id="2c5cf-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="2c5cf-429">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="2c5cf-429">Tables and Views</span></span>  
  
|<span data-ttu-id="2c5cf-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-430">ColumnName</span></span>|<span data-ttu-id="2c5cf-431">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="2c5cf-433">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-433">String</span></span>|  
|<span data-ttu-id="2c5cf-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-434">TABLE_OWNER</span></span>|<span data-ttu-id="2c5cf-435">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-435">String</span></span>|  
|<span data-ttu-id="2c5cf-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-436">TABLE_NAME</span></span>|<span data-ttu-id="2c5cf-437">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-437">String</span></span>|  
|<span data-ttu-id="2c5cf-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-438">TABLE_TYPE</span></span>|<span data-ttu-id="2c5cf-439">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-439">String</span></span>|  
|<span data-ttu-id="2c5cf-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-440">REMARKS</span></span>|<span data-ttu-id="2c5cf-441">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="2c5cf-442">資料行</span><span class="sxs-lookup"><span data-stu-id="2c5cf-442">Columns</span></span>  
  
|<span data-ttu-id="2c5cf-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-443">ColumnName</span></span>|<span data-ttu-id="2c5cf-444">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="2c5cf-446">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-446">String</span></span>|  
|<span data-ttu-id="2c5cf-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-447">TABLE_OWNER</span></span>|<span data-ttu-id="2c5cf-448">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-448">String</span></span>|  
|<span data-ttu-id="2c5cf-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-449">TABLE_NAME</span></span>|<span data-ttu-id="2c5cf-450">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-450">String</span></span>|  
|<span data-ttu-id="2c5cf-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-451">COLUMN_NAME</span></span>|<span data-ttu-id="2c5cf-452">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-452">String</span></span>|  
|<span data-ttu-id="2c5cf-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-453">DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-454">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-454">Int16</span></span>|  
|<span data-ttu-id="2c5cf-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-455">TYPE_NAME</span></span>|<span data-ttu-id="2c5cf-456">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-456">String</span></span>|  
|<span data-ttu-id="2c5cf-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-457">PRECISION</span></span>|<span data-ttu-id="2c5cf-458">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-458">Int32</span></span>|  
|<span data-ttu-id="2c5cf-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c5cf-459">LENGTH</span></span>|<span data-ttu-id="2c5cf-460">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-460">Int32</span></span>|  
|<span data-ttu-id="2c5cf-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-461">SCALE</span></span>|<span data-ttu-id="2c5cf-462">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-462">Int16</span></span>|  
|<span data-ttu-id="2c5cf-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="2c5cf-463">RADIX</span></span>|<span data-ttu-id="2c5cf-464">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-464">Int16</span></span>|  
|<span data-ttu-id="2c5cf-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-465">NULLABLE</span></span>|<span data-ttu-id="2c5cf-466">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-466">Int16</span></span>|  
|<span data-ttu-id="2c5cf-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-467">REMARKS</span></span>|<span data-ttu-id="2c5cf-468">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-468">String</span></span>|  
|<span data-ttu-id="2c5cf-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c5cf-470">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="2c5cf-471">程序</span><span class="sxs-lookup"><span data-stu-id="2c5cf-471">Procedures</span></span>  
  
|<span data-ttu-id="2c5cf-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-472">ColumnName</span></span>|<span data-ttu-id="2c5cf-473">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="2c5cf-475">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-475">String</span></span>|  
|<span data-ttu-id="2c5cf-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="2c5cf-477">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-477">String</span></span>|  
|<span data-ttu-id="2c5cf-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="2c5cf-479">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-479">String</span></span>|  
|<span data-ttu-id="2c5cf-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="2c5cf-481">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-481">Int16</span></span>|  
|<span data-ttu-id="2c5cf-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="2c5cf-483">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-483">Int16</span></span>|  
|<span data-ttu-id="2c5cf-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="2c5cf-485">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-485">Int16</span></span>|  
|<span data-ttu-id="2c5cf-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-486">REMARKS</span></span>|<span data-ttu-id="2c5cf-487">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-487">String</span></span>|  
|<span data-ttu-id="2c5cf-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2c5cf-489">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="2c5cf-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2c5cf-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="2c5cf-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-491">ColumnName</span></span>|<span data-ttu-id="2c5cf-492">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="2c5cf-494">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-494">String</span></span>|  
|<span data-ttu-id="2c5cf-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c5cf-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="2c5cf-496">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-496">String</span></span>|  
|<span data-ttu-id="2c5cf-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="2c5cf-498">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-498">String</span></span>|  
|<span data-ttu-id="2c5cf-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-499">COLUMN_NAME</span></span>|<span data-ttu-id="2c5cf-500">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-500">String</span></span>|  
|<span data-ttu-id="2c5cf-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-501">COLUMN_TYPE</span></span>|<span data-ttu-id="2c5cf-502">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-502">Int16</span></span>|  
|<span data-ttu-id="2c5cf-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-503">DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-504">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-504">Int16</span></span>|  
|<span data-ttu-id="2c5cf-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-505">TYPE_NAME</span></span>|<span data-ttu-id="2c5cf-506">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-506">String</span></span>|  
|<span data-ttu-id="2c5cf-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-507">PRECISION</span></span>|<span data-ttu-id="2c5cf-508">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-508">Int32</span></span>|  
|<span data-ttu-id="2c5cf-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c5cf-509">LENGTH</span></span>|<span data-ttu-id="2c5cf-510">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-510">Int32</span></span>|  
|<span data-ttu-id="2c5cf-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-511">SCALE</span></span>|<span data-ttu-id="2c5cf-512">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-512">Int16</span></span>|  
|<span data-ttu-id="2c5cf-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="2c5cf-513">RADIX</span></span>|<span data-ttu-id="2c5cf-514">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-514">Int16</span></span>|  
|<span data-ttu-id="2c5cf-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-515">NULLABLE</span></span>|<span data-ttu-id="2c5cf-516">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-516">Int16</span></span>|  
|<span data-ttu-id="2c5cf-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-517">REMARKS</span></span>|<span data-ttu-id="2c5cf-518">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-518">String</span></span>|  
|<span data-ttu-id="2c5cf-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="2c5cf-519">OVERLOAD</span></span>|<span data-ttu-id="2c5cf-520">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-520">Int32</span></span>|  
|<span data-ttu-id="2c5cf-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c5cf-522">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="2c5cf-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2c5cf-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="2c5cf-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c5cf-524">ColumnName</span></span>|<span data-ttu-id="2c5cf-525">DataType</span><span class="sxs-lookup"><span data-stu-id="2c5cf-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c5cf-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="2c5cf-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="2c5cf-527">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-527">String</span></span>|  
|<span data-ttu-id="2c5cf-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2c5cf-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="2c5cf-529">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-529">String</span></span>|  
|<span data-ttu-id="2c5cf-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="2c5cf-531">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-531">String</span></span>|  
|<span data-ttu-id="2c5cf-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-532">COLUMN_NAME</span></span>|<span data-ttu-id="2c5cf-533">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-533">String</span></span>|  
|<span data-ttu-id="2c5cf-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-534">COLUMN_TYPE</span></span>|<span data-ttu-id="2c5cf-535">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-535">Int16</span></span>|  
|<span data-ttu-id="2c5cf-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-536">DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-537">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-537">Int16</span></span>|  
|<span data-ttu-id="2c5cf-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c5cf-538">TYPE_NAME</span></span>|<span data-ttu-id="2c5cf-539">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-539">String</span></span>|  
|<span data-ttu-id="2c5cf-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-540">COLUMN_SIZE</span></span>|<span data-ttu-id="2c5cf-541">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-541">Int32</span></span>|  
|<span data-ttu-id="2c5cf-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c5cf-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="2c5cf-543">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-543">Int32</span></span>|  
|<span data-ttu-id="2c5cf-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="2c5cf-545">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-545">Int16</span></span>|  
|<span data-ttu-id="2c5cf-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="2c5cf-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="2c5cf-547">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-547">Int16</span></span>|  
|<span data-ttu-id="2c5cf-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-548">NULLABLE</span></span>|<span data-ttu-id="2c5cf-549">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-549">Int16</span></span>|  
|<span data-ttu-id="2c5cf-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="2c5cf-550">REMARKS</span></span>|<span data-ttu-id="2c5cf-551">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-551">String</span></span>|  
|<span data-ttu-id="2c5cf-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="2c5cf-552">COLUMN_DEF</span></span>|<span data-ttu-id="2c5cf-553">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-553">String</span></span>|  
|<span data-ttu-id="2c5cf-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="2c5cf-555">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-555">Int16</span></span>|  
|<span data-ttu-id="2c5cf-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="2c5cf-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="2c5cf-557">Int16</span><span class="sxs-lookup"><span data-stu-id="2c5cf-557">Int16</span></span>|  
|<span data-ttu-id="2c5cf-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c5cf-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="2c5cf-559">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-559">Int32</span></span>|  
|<span data-ttu-id="2c5cf-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c5cf-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c5cf-561">Int32</span><span class="sxs-lookup"><span data-stu-id="2c5cf-561">Int32</span></span>|  
|<span data-ttu-id="2c5cf-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c5cf-562">IS_NULLABLE</span></span>|<span data-ttu-id="2c5cf-563">String</span><span class="sxs-lookup"><span data-stu-id="2c5cf-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c5cf-564">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c5cf-564">See Also</span></span>  
 [<span data-ttu-id="2c5cf-565">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="2c5cf-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
