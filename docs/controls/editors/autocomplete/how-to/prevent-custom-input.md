---
title: Prevent Custom Input
page_title: Prevent Custom Input  | Kendo UI AutoComplete
description: "Learn how to allow only existing values in a Kendo UI AutoComplete widget."
slug: howto_preventcustominput_autocomplete
---

# Prevent Custom Input

The example below demonstrates how to allow only existing values in a Kendo UI AutoComplete widget.

###### Example

```html
     <div id="example">
      <div id="shipping">
        <label for="countries" class="info">Choose shipping countries:</label>
        <input id="countries" />
        <div class="hint">Start typing the name of an European country</div>
      </div>
      <script>
        $(document).ready(function () {
          var data = [
            "Albania",
            "Andorra",
            "Armenia",
            "Austria",
            "Azerbaijan",
            "Belarus",
            "Belgium",
            "Bosnia & Herzegovina",
            "Bulgaria",
            "Croatia",
            "Cyprus",
            "Czech Republic",
            "Denmark",
            "Estonia",
            "Finland",
            "France",
            "Georgia",
            "Germany",
            "Greece",
            "Hungary",
            "Iceland",
            "Ireland",
            "Italy",
            "Kosovo",
            "Latvia",
            "Liechtenstein",
            "Lithuania",
            "Luxembourg",
            "Macedonia",
            "Malta",
            "Moldova",
            "Monaco",
            "Montenegro",
            "Netherlands",
            "Norway",
            "Poland",
            "Portugal",
            "Romania",
            "Russia",
            "San Marino",
            "Serbia",
            "Slovakia",
            "Slovenia",
            "Spain",
            "Sweden",
            "Switzerland",
            "Turkey",
            "Ukraine",
            "United Kingdom",
            "Vatican City"
          ];

          //create AutoComplete UI component
          $("#countries").kendoAutoComplete({
            dataSource: data,
            filter: "startswith",
            placeholder: "Select country...",
            change: function() {
              var found = false;
              var value = this.value();
              var data = this.dataSource.view();

              for(var idx = 0, length = data.length; idx < length; idx++) {
                if (data[idx] === value) {
                  found = true;
                  break;
                }
              }

              if (!found) {
                this.value("");
                alert("Custom values are not allowed");
              }
            }
          });
        });
      </script>
      <style scoped>
        .info {
          display: block;
          line-height: 22px;
          padding: 0 5px 5px 0;
          color: #36558e;
        }

        #shipping {
          width: 482px;
          height: 152px;
          padding: 110px 0 0 30px;
          background: url('../content/web/autocomplete/shipping.png') transparent no-repeat 0 0;
          margin: 100px auto;
        }

        .k-autocomplete
        {
          width: 250px;
          vertical-align: middle;
        }

        .hint {
          line-height: 22px;
          color: #aaa;
          font-style: italic;
          font-size: .9em;
          color: #7496d4;
        }
      </style>
    </div>
```

## See Also

Other articles on the Kendo UI AutoComplete:

* [AutoComplete JavaScript API Reference](/api/javascript/ui/autocomplete)
* [How to Highlight Matched Values]({% slug howto_highlight_matched_values_autocomplete %})
* [How to Restrict Other Users]({% slug howto_restrict_user_input_autocomplete %})

For more runnable examples on the Kendo UI AutoComplete, browse its [**How To** documentation folder]({% slug howto_use_custom_angularjs_templates_autocomplete %}).
