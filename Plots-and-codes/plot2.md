install.packages("sqldf")
library(sqldf)	
data<-read.csv.sql("household_power_consumption.txt",sql="select * from file where Date in ('1/2/2007','2/2/2007')",header=TRUE,stringsAsFactors=FALSE,sep=';')
dateTime   <- as.POSIXlt(paste(as.Date(data$Date, format="%d/%m/%Y"), data$Time, sep=" "))

png("C:/Users/Ribhu/Statman/Data Science/4. Exploratory Data Analysis/plot2.png",width=480,height=480)
dateTime   <- as.POSIXlt(paste(as.Date(data$Date, format="%d/%m/%Y"), data$Time, sep=" "))
plot(dateTime, data$Global_active_power, type="l", xlab="", ylab="Global Active Power (kilowatts)")
dev.off()
