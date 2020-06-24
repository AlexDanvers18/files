from pprint import pprint


# Задача №1
def make_cook_book(file_name):
    cook_book = {}

    try:
        with open(file_name, encoding='utf-8') as f:
            spisok = [line.strip() for line in f]

        for i, j in enumerate(spisok):
            if j.isdigit():
                cook_book[spisok[i-1]] = []

                for slice in spisok[i+1:i+int(j)+1]:
                    ingr_name = slice.split('|')[0]
                    quantity = int(slice.split('|')[1])
                    measure = slice.split('|')[2]

                    cook_book[spisok[i-1]].append({'ingr_name':ingr_name,
                                                'quantity':quantity,
                                                'measure':measure})
        return cook_book

    except FileNotFoundError:
        return(f'Файл: {file_name} не найден.')
    except Exception as error:
        return f'Ошибка - {error}'


# Задача №2
def get_shop_list_by_dishes(dishes, cooking_book, person_count):
    ing_dict = {}

    for key in cooking_book.keys():
        for dish in dishes:
            if key == dish:
                for dictionary in cooking_book[key]:

                    ing_name = dictionary['ingr_name']

                    try:
                        ing_dict[ing_name]['quantity'] += (dictionary['quantity'] * person_count)
                    except:
                        ing_dict[ing_name] = {'measure': dictionary['measure'],
                                              'quantity': dictionary['quantity'] * person_count}

    return ing_dict



# Задача №1
print('Задача №1:\n')
pprint(make_cook_book('recipes.txt'))
print('\n' * 5)


# Задача №2
print('Задача №2:\n')
pprint(get_shop_list_by_dishes(['Омлет', 'Омлет'], make_cook_book('recipes.txt'), 5))
