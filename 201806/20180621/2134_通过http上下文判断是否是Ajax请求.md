## [通过http上下文判断是否是Ajax请求](https://www.cnblogs.com/tangchun/p/9121334.html)

<div class="postbody">

<div id="cnblogs_post_body" class="blogpost-body">

<div class="cnblogs_code">

``` csharp
    using System;
    
    namespace System.Web.Mvc
    {
        /// <summary>Represents a class that extends the <see cref="T:System.Web.HttpRequestBase" /> class by adding the ability to determine whether an HTTP request is an AJAX request.</summary>
        public static class AjaxRequestExtensions
        {
            /// <summary>Determines whether the specified HTTP request is an AJAX request.</summary>
            /// <returns>true if the specified HTTP request is an AJAX request; otherwise, false.</returns>
            /// <param name="request">The HTTP request.</param>
            /// <exception cref="T:System.ArgumentNullException">The <paramref name="request" /> parameter is null (Nothing in Visual Basic).</exception>
            public static bool IsAjaxRequest(this HttpRequestBase request)
            {
                if (request == null)
                {
                    throw new ArgumentNullException("request");
                }
                return request["X-Requested-With"] == "XMLHttpRequest" || (request.Headers != null && request.Headers["X-Requested-With"] == "XMLHttpRequest");
            }
        }
    }
```
</div>

一直不清楚服务端是如何判断一个请求是否是ajax请求，通过ILSpy查看，才得知是通过判断请求头是否存在

<div class="header-name">

**X-Requested-With:XMLHttpRequest ** 来判断是否是ajax请求。

</div>

</div>

