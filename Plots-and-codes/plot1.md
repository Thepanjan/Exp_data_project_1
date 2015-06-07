install.packages("sqldf")
library(sqldf)	
data<-read.csv.sql("household_power_consumption.txt",sql="select * from file where Date in ('1/2/2007','2/2/2007')",header=TRUE,stringsAsFactors=FALSE,sep=';')

hist(data$Global_active_power, main="Global Active Power", xlab="Global Active Power (kilowatts)", col="orangered2")
