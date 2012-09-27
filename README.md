My-textarea
===========

Dynamic Textarea - automatic content height


Author: PhDr. Matej Lednár, PhD. (c) 2012 

     function createDynamicTextarea() {
        this.style.color = "black";
        var content = this.value;
        var charsAtline = this.cols  * 1; // number conversion
        var lineChecker = content.split(/\n/g);
        var breaks = lineChecker;
        var lineStatus = true;  // line is ok

        // check if exists \n
        if (breaks) {
          breaks = breaks.length;
        }
        else {
          breaks = 1;               // default number of lines
          lineChecker = [];         // default state
          lineChecker[0] = content; // process first line
        }

        for (var i = 0; i < lineChecker.length; i++) {
          var check = lineChecker[i];
          var length = check.length;

          if (length > charsAtline) {
            var tmp = []; // creates new lines
            var leftOver = length % charsAtline;
            for (var j = 0; j < Math.ceil(length / charsAtline); j++) {
              if ((length - (j * charsAtline)) > leftOver ) {
                tmp[j] = check.substring(j * charsAtline, (j + 1) * charsAtline) + "\n";
              }
              else {
                tmp[j] = check.substring((j * charsAtline));
                this.rows = (this.rows * 1) - 1;
              }
              this.rows = (this.rows * 1) + 1;
            }
            lineChecker[i] = tmp.join("");
            this.value = lineChecker.join("\n");            
            lineStatus = false;   // line and all content were updated
          }
        }
        if (lineStatus) {
          this.rows = breaks;
        }
      }


Webs: 
- work.mldgroup.com
- expertcode.mldgroup.com /* will be replaced by howto */
- howto.mldgroup.com
     