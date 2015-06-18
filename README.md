## Put comments here that give an overall description of what your
## functions do

## Write a short comment describing this function

# This function creates a list containing a function to
# 1.set the value of the matrix
# 2.get the value of the matrix
# 3.set the value of the inverted matrix
# 4.get the value of the inverted matrix


makeCacheMatrix <- function(x = numeric()) {
      m <- NULL
      set <- function(y) {
            x <<- y
            m <<- NULL
      }
      get <- function() x
      setInverse <- function(solve) m <<- solve
      getInverse <- function() m
      list(set = set, get = get,
           setInverse = setInverse,
           getInverse = getInverse)
}

# This function first checks if the inverted matrix is already calculated.
# If yes, it returns the inverted matrix and stops. If not, it calculates
# The inverted matrix and returns is, and sets the flag for inverted matrix 
# calculated 	

## Write a short comment describing this function

cacheSolve <- function(x, ...) {
      m <- x$getInverse()
      if(!is.null(m)) {
            message("getting cached data")
            return(m)
      }
      data <- x$get()
      m <- solve(data, ...)
      x$setInverse(m)
      m
}


# example of program working

x<- matrix (c(100,0,0,100), nrow=2, ncol=2)
print (x)
z<-makeCacheMatrix (x)
print (z)
cacheSolve (z)
# repeat to make sure cache works
cacheSolve (z)
