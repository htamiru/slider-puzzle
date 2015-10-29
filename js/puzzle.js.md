(function () {
    $("td").click(tileClick);
    console.log(checkForWin());
      
    function isEmptySquare($image) {
        var altText = $image.attr("alt");
        if (altText === "empty") {
            return true;
        } else {
            return false;
        }
    }
function tileClick() {
        var $td, $clickImg, $emptyImg, temp;
        $td = $(this)
    
        $clickedImg = $td.children().first();
        if (isEmtySquare($clickedImg)) {
            alert("click on an image next to this square to move it.");
        } else {
            $emptyImg = checkForEmpty($td);
            console.log($emptyImg);
            if ($emptyImg === null) {
                alert("click on an image next to this square to move it.");
        
            } else {
        
                temp = $clickedImg.attr("src");
                $clickedImg.attr("src", $emptyImg.attr("src"));
                $emtyImg.attr("src", temp);
            
                temp = $clickedImg.attr("alt");
                $clickedImg.attr("alt", $emptyImg.attr("alt"));
                $emtyImg.attr("alt", temp);
                if (checkForWin()){
                    $("puzzleGrid").addClass("win");
            }
        }
    }
        
    function checkForEmty($td) {
    var newRow, newCol, idToCheck, $img;
    var id = $td.attr("id")
    var row = id.substring(4,5);
    var col = id.substring(5,6);
    console.log("Row " + row);
    console.log("Col "+ col);
    
    if (row > 1) {
        newRow = parseInt(row)-1;
        newCol = col;
        idToCheck = "#cell" + newRow + newCol;
            return $img;
        }
    }
    if (row < 4){
        newRow = parseIntrow + 1;
        newCol = col;
         idToCheck = "#cell" + newRow + newCol;
            return $img;
        }
    }
    
       if (col > 1) {
        newRow = row;
        newCol = parseInt(col) -1;
        idToCheck = "#cell" + newRow + newCol;
            return $img;
        }
    } 
    
       if (col <4){
        newRow = row;
        newCol = parseInt(col) +1;
       idToCheck = "#cell" + newRow + newCol;
            return $img;
        }
    } 
    return null;
        }
    
    function getImageFromCell (row, col){
        idToCheck = "#cell" + row + col;
        console.log("Id below: " +idToCheck);         
        return $(idToCheck).children().first();
            }
    function checkForWin() {
    var i, counter, $allImages, $currentImage;
    counter = 1;
    $allImages = $("img").each(Function(index, Element) {
    var altText = $(this).attr("alt");
        if (counter === 16){
            if (altText !="empty") {
                
            isWin = false;
            return false;
            }
            }
            
            else {
                if (altText != counter) {
                isWin = false;
                return false;
                }
        }
        counter = counter + 1;
        });
        return isWin;
            
    
                               


        }());