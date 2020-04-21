class Store:
    
    def __init__(self, item = None):
        self.items = []
        pass
    
    def add_item(self, item = None):
        self.items.append(item)
        
    def filter(self, query_obj):
        store = Store()
        filtered_obj = eval('Query.' + query_obj.operation + '(query_obj, self.items)')
        for item in filtered_obj:
            store.add_item(item)
        return store
     
    def exclude(self, query_obj):
        store = Store()
        filtered_obj = eval('Query.' + query_obj.operation + '(query_obj, self.items)')
        for item in self.items:
            if item not in filtered_obj:
                store.add_item(item)
        return store
    
    def count(self):
        return len(self.items)
    
    def __str__(self):
        results = ''
        if self.items == []:
            return f'No items'
        results += '\n'.join(map(str, self.items))
        return results
        

class Item:
    def __init__(self, name = None, price = 0, category = None):
        self._name = name
        if price <= 0:
            raise ValueError(f'Invalid value for price, got {price}')
        self._price = price
        self._category = category
    
    def __str__(self):
        return f'{self.name}@{self.price}-{self.category}'
    
    @property
    def name(self):
        return self._name
    
    @property
    def price(self):
        return self._price
        
    @property
    def category(self):
        return self._category

         
class Query:
    
    operations = ['IN', 'EQ', 'GT', 'GTE', 'LT', 'LTE', 'STARTS_WITH', 'ENDS_WITH', 'CONTAINS']
    
    def __init__(self, field=None, value=None, operation=None):
        self._field = field
        self._value = value
        if operation not in Query.operations:
            raise ValueError(f'Invalid value for operation, got {operation}')
        self._operation = operation
    
    @property
    def field(self):
        return self._field
    
    @property
    def value(self):
        return self._value
        
    @property
    def operation(self):
        return self._operation
    
    
    def __str__(self):
        return f'{self.field} {self.operation} {self.value}'
    
    def EQ(self, items_list):
        obj = []
        for item in items_list:
            if eval('item.'+ self.field) == self.value:
                obj.append(item)
        return obj
    
    def GT(self, items_list):
        obj = []
        for item in items_list:
            if eval('item.' + self.field) > self.value:
                obj.append(item)
        return obj
    
    def GTE(self, items_list):
        obj = []
        for item in items_list:
            if eval('item.' + self.field) >= self.value:
                obj.append(item)
        return obj
    
    def LT(self, items_list):
        obj = []
        for item in items_list:
            if eval('item.' + self.field) < self.value:
                obj.append(item)
        return obj
    
    def LTE(self, items_list):
        obj = []
        for item in items_list:
            if eval('item.' + self.field) <= self.value:
                obj.append(item)
        return obj
    
    def STARTS_WITH(self, items_list):
        obj = []
        length = len(self.value)
        for item in items_list:
            if eval('item.' + self.field)[:length] == self.value:
                obj.append(item)
        return obj
    
    def ENDS_WITH(self, items_list):
        obj = []
        length = len(self.value) + 1
        for item in items_list:
            if eval('item.' + self.field)[:-length:-1] == self.value[::-1]:
                obj.append(item)
        return obj
    
    def CONTAINS(self, items_list):
        obj = []
        for item in items_list:
            if self.value in eval('item.' + self.field):
                obj.append(item)
        return obj
    
    def IN(self, items_list):
        obj = []
        for item in items_list:
            if eval('item.' + self.field) in self.value:
                obj.append(item)
        return obj
        
--------------------------------------------------------------------------------------------------------------------------

Tests ran at 21 Apr 02 39 PM

52 tests passed out of 52 tests.

test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_print_item: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_when_print_two_items: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_when_price_is_zero: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_when_price_is_negative: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_print_query: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_when_printing_two_query: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_invalid_value_for_query_operation: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_add_items_to_store: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_creating_two_stores: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_print_empty_store: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_print_items_in_store: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_eq_name_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_eq_price_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_eq_category_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_in_name_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_in_price_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_in_category_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_gt_price_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_gte_price_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_gte_price_field_equal_case: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_lt_price_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_lte_price_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_lte_price_field_equal_case: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_starts_with_name_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_starts_with_category_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_ends_with_name_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_ends_with_category_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_contains_name_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_filter_contains_category_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_store_after_filter: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_eq_name_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_eq_price_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_eq_category_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_in_name_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_in_price_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_in_category_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_gt_price_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_gte_price_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_gte_price_field_equal_case: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_lt_price_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_lte_price_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_lte_price_field_equal_case: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_starts_with_name_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_starts_with_category_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_ends_with_name_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_ends_with_category_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_contains_name_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_exclude_contains_category_field: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_store_after_exclude: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_chained_filters: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_chained_filter_and_exclude: passed
test_81d6cb5b-2c92-40eb-be30-281960d59f0d_store.py::test_count_store_items: passed


Errors: 0 errors

