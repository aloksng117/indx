#Option one: direct link to JS event
<script type="text/javascript">
    document.getElementById("myButton").onclick = function () {
        location.href = "http://www.google.com";
    };
</script>

```{r, echo=F}
actionButton("myButton", "Redirect")
```

#Option two: dedicate redirect js, triggered by shinyjs
<script type="text/javascript">
    go_away = function () {
        location.href = "http://www.google.com";
    };
</script> 

```{r, echo=F}
shinyjs::useShinyjs(rmd = TRUE)
actionButton("myButton2", "Redirect!!")

observeEvent(input$myButton2, {
  shinyjs::runjs('go_away()')
})

```
