import csv

with open('space.txt', encoding='utf8') as file, \
    open('space_new.txt', 'w', encoding='utf8', newline='') as file_new:
    reader = csv.DictReader(file, Delimiter="*")
    writer_new = csv.DictWriter(file_new, ['ShipName', 'planet', 'coord place', 'directing'])
    writer_new.writeheader()
    for row in reader:
        n = int(row['ShipName'][5])
        m = int(row['ShipName'][6])
        koord = row['coord_place'].split()
        t = len(row['planet'])
        xd = int(koord[0])
        yd = int(koord[1])
    if n > 5:
        x = n + xd
    else:
        x = -(n + xd)*4 + t
    if m > 3:
        y = m + t + yd
    else:
        y = -(n + yd)*m
    row['coord_place'] = str(x) + '' + str(y)
    if row['ShipName'] [3] == 'V':
        print(row['Shipname'] + ' -(' + str(x) + "," + str(y) + ')' )
        writer_new.writerow(row)

