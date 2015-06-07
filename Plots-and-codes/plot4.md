install.packages("sqldf")
library(sqldf)	
data<-read.csv.sql("household_power_consumption.txt",sql="select * from file where Date in ('1/2/2007','2/2/2007')",header=TRUE,stringsAsFactors=FALSE,sep=';')
dateTime   <- as.POSIXlt(paste(as.Date(data$Date, format="%d/%m/%Y"), data$Time, sep=" "))

png("C:/Users/Ribhu/Statman/Data Science/4. Exploratory Data Analysis/plot4.png",width=480,height=480)

par(mfrow=c(2,2))

plot(dateTime, data$Global_active_power, type="l", xlab="", ylab="Global Active Power (kilowatts)")

plot(dateTime, data$Voltage, type="l", xlab="datetime", ylab="Voltage")

plot(dateTime, data$Sub_metering_1, type="l", xlab="", ylab="Energy Sub Metering", col="black") 
par(new=TRUE)
lines(dateTime, data$Sub_metering_2, type="l", col="red") 
par(new=TRUE)
lines(dateTime, data$Sub_metering_3, type="l", col="blue")

legend("topright", col=c("black", "red", "blue"), lty=1, lwd=2, bty="n", legend=c("Sub_metering_1", "Sub_metering_2", "Sub_metering_3"))


plot(dateTime, data$Global_reactive_power, type="l", xlab="dateTime", ylab="Global_reactive_power")

dev.off()
