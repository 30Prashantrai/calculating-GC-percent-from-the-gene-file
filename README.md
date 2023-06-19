# calculating-GC-percent-from-the-gene-file
the code will calculate GC percent from the txt file where there are many gene bases or lines and from each bases it will give the letters GC  percentange and gives a visual of it using scatterplot.

f = open(r"D:\Download\gene.txt","r")
content = f.readlines()
f.close()
print(len(content[1]))
#result = {"base1":{"A":?, "T":?, "C":?, "G":?}}
print (len(content[0].strip()))
print (content[0])
result = {"base%s"%(i):{"A":0, "T":0,"G":0, "C":0} for i in range(1, len(content[0].strip())+1, 1)}
line_no = 1
for row in content:
    base_no = 1
    row = row.strip()
    for n in row:
        n = n.upper()
        #print (line_no, base_no, n)
        result["base%s"%(base_no)][n] += 1
        base_no += 1
    line_no += 1

GC_percent = {x:round((result[x]["G"] + result[x]["C"]) / sum(result[x].values()) * 100,2 ) for x in result}
print (GC_percent)

import matplotlib.pyplot as plt

x = list(GC_percent.keys())
y = list(GC_percent.values())
f = plt.figure()
f.set_figwidth(20)
f.set_figheight(5)

plt.plot(x,y,'or')
plt.xticks(rotation = 90)
plt.savefig(r"D:\Downloads\gene.png")
plt.show()
