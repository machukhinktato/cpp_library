template<class T>
class Auto_ptr5
{
	T* m_ptr;
public:
	Auto_ptr5(T* ptr = nullptr)
		:m_ptr(ptr)
	{
	}
 
	~Auto_ptr5()
	{
		delete m_ptr;
	}
 
	// Конструктор копирования - запрещаем любое копирование!
	Auto_ptr5(const Auto_ptr5& x) = delete;
 
	// Конструктор перемещения, который передает право собственности на x.m_ptr в m_ptr
	Auto_ptr5(Auto_ptr5&& x)
		: m_ptr(x.m_ptr)
	{
		x.m_ptr = nullptr;
	}
 
	// Оператор присваивания копированием - запрещаем любое копирование!
	Auto_ptr5& operator=(const Auto_ptr5& x) = delete;
 
	// Оператор присваивания перемещением, который передает право собственности на x.m_ptr в m_ptr
	Auto_ptr5& operator=(Auto_ptr5&& x)
	{
		// Проверка на самоприсваивание
		if (&x == this)
			return *this;
 
		// Удаляем всё, что может хранить указатель до этого момента
		delete m_ptr;
 
		// Передаем право собственности на x.m_ptr в m_ptr
		m_ptr = x.m_ptr;
		x.m_ptr = nullptr;
 
		return *this;
	}
 
	T& operator*() const { return *m_ptr; }
	T* operator->() const { return m_ptr; }
	bool isNull() const { return m_ptr == nullptr; }
};
